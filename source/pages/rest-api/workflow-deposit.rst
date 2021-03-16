.. _rest-api-workflow-deposits:

**************
REST API workflow for deposits
**************

This page provides information about creating and managging deposit using the REST API of the Data Repository service.

.. contents::
    :depth: 4

.. _rest-api-general-workflow:

==================
General publication workflow
==================

The HTTP REST API does not impose a specific workflow for creating a deposit, but some steps need to be taken in order independently from each other. The following example workflow only defines the most basic steps:

- Identify a target community for your data by using the REST API :ref:`List all communities <rest-api-ref-list-all-communities>` request
- Using the community's identifier, retrieve the JSON Schema of the deposit's metadata. The submitted metadata will have to conform to this schema. Use the :ref:`Get community schema <rest-api-ref-get-community-schema>` request.
- Create a draft deposit: use the :ref:`Create draft deposit <rest-api-ref-create-draft-deposit>` request.
- Upload the files into the draft deposit. You will have to use one HTTP request per file. Use the :ref:`Upload file <rest-api-ref-upload-file-into-draft-deposit>` request.
- Set the complete metadata and publish the deposit. Use the :ref:`Submit draft for publication <rest-api-ref-submit-draft-deposit-for-publication>` request.

.. _rest-api-preparation:

==================
Preparation
==================

When your dataset is ready for publication, it can be uploaded to the Data Repository service by creating a draft deposit and adding files and metadata. This page will guide you through the creation process of a new draft deposits, preparing and finally publishing it as a deposit. It covers:

 - The creation of a new draft deposit,
 - The addition and removal of files and metadata, and
 - Committing the draft deposit to publish it

Please note that the Data Repository service makes a distinction between the two terms `deposit` and `draft deposit` (or simply `draft`). A **deposit** is published and therefore unchangeable and has persistent identifiers (PID) assigned to it, as well as checksums. A user can create a deposit by **first creating a draft deposit**, which is modifiable. Files and metadata can be placed into a draft deposit, but not into an already published deposit.

.. _rest-api-deposit-workflow:

==================
Deposit workflow
==================

In the following diagram the general deposit workflow of Data Repository is shown. All blue boxes require a request interaction with the Data Repository service.

 .. image:: ../img/deposit-workflow.png
   :align: center
   :width: 75%

The red boxes indicate an object state, where in this workflow only draft, submitted and published deposits exist. Files and metadata can be added multiple times. Persistent identifiers (PIDs) and checksum are automatically added by Data Repository (green boxes). Once a draft deposit is committed, depending on the community's requirements, the deposit is either in submitted state and needs further approval or is immediately published.

.. _rest-api-create-new-draft-deposit:

==================
Create a new draft deposit
==================

After loading your token a **POST** request will create a new draft deposit. Only some basic metadata is needed, like the title and community, which is sent along with the request as the data argument together with a header defining the content type. All metadata can be changed later during the deposit workflow.

In the following example, a new open access deposit is created for the EUDAT community with the title 'My test upload'. The community is identified using its unique identifier:

.. code-block:: python

    >>> header = {"Content-Type": "application/json"}
    >>> metadata = {"titles": [{"title":"My test upload"}],
                    "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
                    "open_access": True}
    >>> r = requests.post('https://$SDR_HOST/api/deposits/', params={'access_token': token}, data=json.dumps(metadata), headers=header)

On success, the response status code and text will be different this time:

.. code-block:: json

    {
      "created": "2017-03-02T16:34:26.383505+00:00",
      "id": "b43a0e6914e34de8bd19613bcdc0d364",
      "links": {
        "files": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa",
        "publication": "https://$SDR_HOST/api/deposits/b43a0e6914e34de8bd19613bcdc0d364",
        "self": "https://$SDR_HOST/api/deposits/b43a0e6914e34de8bd19613bcdc0d364/draft"
      },
      "metadata": {
        "$schema": "https://$SDR_HOST/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095/schemas/0#/draft_json_schema",
        "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
        "community_specific": {},
        "open_access": true,
        "owners": [
          10
        ],
        "publication_state": "draft",
        "titles": [
          {
            "title": "My test upload"
          }
        ]
      },
      "updated": "2017-03-02T16:34:26.383514+00:00"
    }

Response code 201 indicates the draft deposit has been successfully created. The deposit identifier metadata field `id` in the response text is used to identify the draft deposit during the additional steps of adding files and metadata:

.. code-block:: python

    >>> result = json.loads(r.text)
    >>> depositid = result["id"]
    >>> print(depositid)
    b43a0e6914e34de8bd19613bcdc0d364


The deposit is still in a draft state, as is indicated in the `publication_state` property:

.. code-block:: python

    >>> print(result["metadata"]["publication_state"])
    draft

After creation, the next steps are to add files and metadata. This can be done in any order and repeatedly after each addition until the draft deposit is finally published. In the next sections, both procedures are explained.

Please note that the deposit identifier will remain the same during the draft stage and after finally publishing the deposit. There is no attached EPIC PID yet.

.. _rest-api-add-files-draft-deposit:

Add files to your new draft deposit
---------------------

After creation of the draft deposit, files can be added. This is achieved in a similar way as the previous example via a PUT request. Make sure your data files are accessible in the Python session. In this case the files named `sequence.txt` and `sequence2.txt` are added to the draft deposit. For every file to add to the deposit, a separate request is required.

Files in deposits are placed in file buckets attached to a deposit with a specific `file_bucket_id`. This identifier can be extracted from the returned information after creating the draft deposit in the nested property `files` of the property `links`:

.. code-block:: python

    >>> filebucketid = result["links"]["files"].split('/')[-1]
    >>> print(filebucketid)
    0163d244-5845-40ca-899c-d1d0025f68aa

First, define a file open handle to send along with the request, e.g. for the `sequence.txt` file:

.. code-block:: python

    >>> upload_file = open('sequence.txt', 'rb')

In this statement, the action of reading the file is not actually performed. The file will be read only when the request is done and send as a direct data stream.

Define the request URL by adding the file bucket identifier to the `files` end point and define the request header:

.. code-block:: python

    >>> url = 'https://$SDR_HOST/api/files/' + filebucketid
    >>> params = {'access_token': token}
    >>> header = {"Accept": "application/json", "Content-Type": "application/octet-stream"}

The complete put request looks as follows:

.. code-block:: python

    r = requests.put(url + '/sequence.txt', data=upload_file, params=params, headers=header)

If the request is successful, the result can be checked:

.. code-block:: python

	>>> print(r.status_code)
    200
    >>> result = json.loads(r.text)
    >>> print(json.dumps(result, indent=4))
    {
        "mimetype": "text/plain",
        "updated": "2017-03-02T16:40:14.672198+00:00",
        "links": {
            "self": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa/sequence.txt",
            "version": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa/sequence.txt?versionId=c616c2c8-531f-4c00-91d8-c0a5c996194f",
            "uploads": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa/sequence.txt?uploads"
        },
        "is_head": true,
        "created": "2017-03-02T16:40:14.668025+00:00",
        "checksum": "md5:e617f15cd8bded0c4e92e35b5af1609d",
        "version_id": "c616c2c8-531f-4c00-91d8-c0a5c996194f",
        "delete_marker": false,
        "key": "sequence.txt",
        "size": 440
    }


The mime-type is detected, direct links are given and a checksum is calculated. The `version_id` can be used to refer to this specific upload of the file in case new versions are uploaded later on.

If the request fails, check the error by displaying the response text, for example when the `files` object has errors. The reponse text will, in this case, a HTML page describing the error.

When the upload file is not accessible:

.. code-block:: python

	>>> print(r.status_code)
    400
    >>> result = json.loads(r.text)
    >>> print(json.dumps(result, indent=4))
    {
        "status": 400,
        "message": "The browser (or proxy) sent a request that this server could not understand."
    }

Repeat the above steps to add other files.

.. _rest-api-check-uploaded-files:

Check your uploaded files
~~~~~~~~~~~~~~~~~~~~~~~

When all your files have been uploaded, you can check the draft deposit's current status regarding these files using the URL with a GET request:

.. code-block:: python

	>>> r = requests.get('https://$SDR_HOST/api/files/' + filebucketid, params=params)
    >>> result = json.loads(r.text)
    >>> print(json.dumps(result, indent=4))

.. code-block:: json
    {
        "max_file_size": 1048576000,
        "updated": "2017-03-02T16:42:48.980058+00:00",
        "locked": false,
        "links": {
            "self": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa",
            "uploads": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa?uploads",
            "versions": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa?versions"
        },
        "created": "2017-03-02T16:34:26.405147+00:00",
        "quota_size": null,
        "id": "0163d244-5845-40ca-899c-d1d0025f68aa",
        "contents": [
            {
                "mimetype": "text/plain",
                "updated": "2017-03-02T16:42:48.974457+00:00",
                "links": {
                    "self": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa/sequence2.txt",
                    "version": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa/sequence2.txt?versionId=5c13ccc5-d0c4-4e81-b4ba-42a5e6ab4432",
                    "uploads": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa/sequence2.txt?uploads"
                },
                "is_head": true,
                "created": "2017-03-02T16:42:48.970708+00:00",
                "checksum": "md5:0f8d51036979343c38dcc291c18dae7e",
                "version_id": "5c13ccc5-d0c4-4e81-b4ba-42a5e6ab4432",
                "delete_marker": false,
                "key": "sequence2.txt",
                "size": 4042
            },
            {
                "mimetype": "text/plain",
                "updated": "2017-03-02T16:40:14.672198+00:00",
                "links": {
                    "self": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa/sequence.txt",
                    "version": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa/sequence.txt?versionId=c616c2c8-531f-4c00-91d8-c0a5c996194f",
                    "uploads": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa/sequence.txt?uploads"
                },
                "is_head": true,
                "created": "2017-03-02T16:40:14.668025+00:00",
                "checksum": "md5:e617f15cd8bded0c4e92e35b5af1609d",
                "version_id": "c616c2c8-531f-4c00-91d8-c0a5c996194f",
                "delete_marker": false,
                "key": "sequence.txt",
                "size": 440
            }
        ],
        "size": 4482
    }

The links to the file bucket is displayed, as well as the 'contents' list of two files, including the files' sizes. You can do this with every file bucket, as long as you have the file bucket identifier.

.. _rest-api-delete-file-from-draft-deposit:

Delete a file from a draft deposit
~~~~~~~~~~~~~~~~~~~~~~~

In case you've uploaded the wrong file to a draft deposit, you can delete this file as long as the deposit is in draft state. Data Repository supports deletion of files in draft deposits by the owner of that deposit or the site administrator.

In order to delete a file from a draft deposit, a request header and your access token are required:

.. code-block:: python

	>>> header = {"Content-Type": 'application/json'}
    >>> params = {"access_token": token}


To make the request, the file bucket deposit identifier of the draft deposit and the file name under which you've stored the file are required. Along with the DELETE request operation with the `/api/files/<file_bucket_id>/<file_name>` endpoint in the URL, the request then looks as follows:

.. code-block:: python

	>>> url = "https://$SDR_HOST/api/files/513527a8-d3ac-4bd8-a6b0-f8fec9a94cf8/TestFile.txt"
    >>> r = requests.delete(url, params=params, headers=header)


On a successful request, the response code should be 204 while there is no response message:

.. code-block:: python

	>>> print(r)
    <Response [204]>
    >>> print(r.text)

.. _rest-api-add-metadata-draft-deposit:

Add metadata to your draft deposit
~~~~~~~~~~~~~~~~~~~~~~~

Metadata is added to a draft deposit while creating the initial object. By issuing a HTTP patch request with a JSON patch list of operations the current metadata of a deposit can be updated with additional or updated metadata fields and corresponding values.

Since this procedure is quite extensive, refer to the [Update deposit metadata](06_Update_deposit_metadata.md) guide to update your draft deposit's current metadata. This module can also be used to update metadata of existing deposits.

To see how you can fully employ the metadata schema of a community, refer to the [Updating all community metadata fields](06_Update_deposit_metadata.md#updating-all-community-metadata-fields) section of that same guide.

Add references to external files to your draft deposit
~~~~~~~~~~~~~~~~~~~~~~~

It is possible to add files to a deposit that are not stored in Data Repository, but this is not recommended due to the fact that Data Repository cannot guarantee the existence of the files at an external location. Although EPIC PIDs must be used to reference to these files, Data Repository cannot manage or update these PIDs when necessary. The service will also not generate these PIDs as needed, this is left to the user.

Externally referenced files are not added as files, but as separate metadata and therefore need to be provided as a JSON Patch.

If you have a list of files that can be accessed using an EPIC PID, a JSON Patch must used to add these files to the file listing of the Data Repository deposit. For example, if two files are added, the list must be defined as follows:

.. code-block:: python

	>>> external_files = [{
        "key": "Filename1.dat",
        "ePIC_PID": "prefix/suffix-file-name-1"
        },
        {
            "key": "Filename2",
            "ePIC_PID": "prefix/suffix-file-name-2"
        }]


The file names (`key`) of each file does not necessarily have to match the file name provided in the EPIC PIDs, but this is highly recommended in order to not confuse any other user downloading these files.

Using this list, create a JSON Patch as described in [Create a JSON Patch](06_Update_deposit_metadata.md#creating-a-json-patch) and submit it following the steps described in [Submitting the patch](06_Update_deposit_metadata.md#submitting-the-patch).

.. _rest-api-publish-draft-deposit:

==================
Publishing your draft deposit
==================

The final step will complete the draft deposit by altering it using a patch request. After this request, the files of the deposit are immutable and your deposit is published!

In this case, the only thing that needs to be changed is the value of the `publication_state` metadata field. The metadata field will be set to 'submitted', and therefore the patch can be created directly as a string. Also, the header of the request is set:

.. code-block:: python

	>>> header = {'Content-Type': 'application/json-patch+json'}
    >>> commit = '[{"op": "add", "path":"/publication_state", "value": "submitted"}]'

The final commit request will return the updated object metadata in case the request is successful (status code 200):

.. code-block:: python

	>>> url = "https://$SDR_HOST/api/deposits/" + depositid + "/draft"
    >>> r = requests.patch(url, data=commit, params=params, headers=header)
    >>> print(r)
    <Response [200]>
    >>> result = json.loads(r.text)
    >>> print(json.dumps(result, indent=4))
    {
        "updated": "2017-03-02T17:07:13.958052+00:00",
        "metadata": {
            "community_specific": {},
            "publication_state": "published",
            "open_access": true,
            "DOI": "http://doi.org/10.5072/b2share.b43a0e6914e34de8bd19613bcdc0d364",
            "language": "en_GB",
            "publisher": "EUDAT",
            "ePIC_PID": "http://hdl.handle.net/11304/ab379f3b-8ff2-41ff-a96b-a3a066cc820c",
            "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
            "titles": [
                {
                    "title": "My test upload"
                }
            ],
            "contact_email": "email@example.com",
            "descriptions": [
                {
                    "description": "My first dataset ingested using the Data Repository API",
                    "description_type": "Abstract"
                }
            ],
            "owners": [
                10
            ],
            "$schema": "https://$SDR_HOST/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095/schemas/0#/draft_json_schema"
        },
        "id": "b43a0e6914e34de8bd19613bcdc0d364",
        "links": {
            "files": "https://$SDR_HOST/api/files/0163d244-5845-40ca-899c-d1d0025f68aa",
            "self": "https://$SDR_HOST/api/deposits/b43a0e6914e34de8bd19613bcdc0d364/draft",
            "publication": "https://$SDR_HOST/api/deposits/b43a0e6914e34de8bd19613bcdc0d364"
        },
        "created": "2017-03-02T16:34:26.383505+00:00"
    }


Your draft deposit is now published as a new deposit and is available under the URL `https://$SDR_HOST/api/deposits/b43a0e6914e34de8bd19613bcdc0d364`! Please note that after a successful request the metadata returned is that of the draft deposit. You need to do another request to the published deposit to get its metadata.

An EPIC persistent identifier and DOI (`ePIC_PID` and `DOI` fields) have been automatically generated and added to the metadata. The `owners` field array contains the internal user IDs.

Important
~~~~~~~~~~~~~~~~~~~~~~~

A published deposit will always have a draft deposit equivalent. If you ever want to change any of the deposits metadata, then the draft deposit can be immediately used for this process.

Please note that the file bucket identifier of the draft deposit differs from the file bucket identifier of the published deposit. By retrieving the published deposit metadata, the new file bucket identifier can be obtained from the corresponding URL:

.. code-block:: python

	>>> r = requests.get('https://$SDR_HOST/api/deposits/' + depositid)
    >>> result = json.loads(r.text)
    >>> filebucket = result["links"]["files"]
    >>> print(filebucket)
    https://$SDR_HOST/api/files/c1422a22-b8d4-42d6-9e94-1e5590294cb4

Using this URL the state of the file bucket of the published deposit can be investigated. It contains the exact same files as the draft version, but it is locked and therefore cannot be changed anymore:

.. code-block:: python

	>>> r = requests.get(filebucket)
    >>> result = json.loads(r.text)
    >>> print(result["locked"])
    True

.. _rest-api-check-and-display-results-deposit:

==================
Check and display your results
==================

Once the deposit process is completed, the results can be checked by requesting the deposit data using the new deposit identifier. Follow the [deposit retrieval guide](01_Retrieve_existing_deposit.md) for an extensive description on how to do this.

The deposit identifier `id` in the response message can directly be used to see the landing page of the newly created deposit: [b43a0e6914e34de8bd19613bcdc0d364](https://$SDR_HOST/deposits/b43a0e6914e34de8bd19613bcdc0d364). If the page displays a restriction message, this is due the server-side processing of the ingestion. As soon as this is finished, the message will disappear.

Unfortunately, some of the metadata schema fields are missing since during the metadata update step, these fields were not added to the patch. It is highly recommended to complete all fields during this step in order to increase the discoverability, authenticity and reusability of the dataset. Please check the [Update deposit metadata](06_Update_deposit_metadata.md) module to update your published deposit's metadata.

