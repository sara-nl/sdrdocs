.. _rest-api-ref:

**************
REST API reference
**************

In this page all available REST API requests are listed, together with examples. In all examples, the training instance of the Data Repository is used.

.. contents::
    :depth: 4

.. _rest-api-ref-structure:

==============
Structure
==============

Each allowed request is described as follows:

- Description - A description of the function of the request.

- HTTP method - which HTTP protocol such as ``GET`` or ``POST`` method is used.

- URL path - grammar for the allowed paths used together with one of the base URLs above.

- Status code - the returned status code upon a successful request.

- Returns - the returned data in the body of the response upon a successful request.

- Example - an example of usage using the program curl from the command line.

Some of the requests additionally might have the following information:

- Required parameters - the parameters that need to be added to the URL.

- Required data - the data that needs to be sent with the request, the expected structure is shown in the example.

Variables in the descriptions:

- ``SDR_HOST`` - the host of the instance used for interaction

- ``TOKEN`` - your personal access token used for authentication

- ``NAMESPACE_ID`` - namespace for a specific object

- ``OBJECT_ID`` - identifier for a specific object, which can be in draft or published state

- ``DEPOSIT_ID`` - identifier for a specific deposit, which can be in draft or published state

- ``COLLECTION_ID`` - identifier for a specific collection, which can be in draft or published state

- ``COMMUNITY_ID`` - identifier of a user community in Data Repository

- ``SCHEMA_ID`` - identifier of a metadata schema in Data Repository

- ``FILE_NAME`` - name of a file in a specific file bucket

- ``FIELD_NAME`` - name of a metadata field

For most requests, an example is shown using a cURL command. If a payload is sent with the request, this is shown in a structured way below the example. The returned response body and request-specific errors are shown if applicable.

.. _rest-api-ref-object-retrieval:

==============
Object retrieval
==============

The following requests concern the retrieval of information about deposits and communities.

.. _rest-api-ref-list-all-communities:

List all communities
______________________

List all the communities, without any filtering.

- HTTP method: ``GET``

- URL path: ``/api/objects/community``

- URL alias: ``/api/communities``

- Required parameters: None

- Status code on success: ``200``

- Returns: the list of communities (in JSON format) or an error message.

Command:

``curl "https://$SDR_HOST/api/objects/community"``

Returns (example):

.. code-block:: json

  [
    {
      "id": "astrophysics",
      "created": "2020-04-12T16:25:26.064000Z",
      "properties": {
        "pid": "community:astrophysics",
        "namespace": "community",
        "type": "Community",
        "state": "Published",
        "sharelevel": "Open"
      },
      "metadata": {
        "base": {
          "title": "Astrophysics",
          "description": "This is the Astrophysics community"
        }
      },
      "links": {
        "self": "https://$SDR_HOST/api/objects/community/astrophysics"
      }
    },
    {
      "id": "surf",
      "created": "2020-04-12T16:25:28.420000Z",
      "properties": {
        "pid": "community:surf",
        "namespace": "community",
        "type": "Community",
        "state": "Published",
        "sharelevel": "Open"
      },
      "metadata": {
        "base": {
          "title": "SURF",
          "description": "This is the SURF community"
        }
      },
      "links": {
        "self": "https://$SDR_HOST/api/objects/community/surf"
      }
    },
    {
      "id": "lofar",
      "created": "2020-05-18T12:50:21.340000Z",
      "properties": {
        "pid": "community:lofar",
        "namespace": "community",
        "type": "Community",
        "state": "Published",
        "sharelevel": "Open"
      },
      "metadata": {
        "base": {
          "title": "LOFAR",
          "description": "This is the LOFAR community"
        }
      },
      "links": {
        "self": "https://$SDR_HOST/api/objects/community/lofar"
      }
    }
  ]


.. _rest-api-ref-list-deposits-per-community:

List all community deposits
______________________

List all deposits of a specific community.

- HTTP method: ``GET``

- URL path: ``/api/objects/community/$COMMUNITY_ID/deposits``

- Required parameters: None

- Status code on success: ``200``

- Returns: the list of deposits (in JSON format) or an error message

Command:

``curl "https://$SDR_HOST/api/objects/community/$COMMUNITY_ID/deposits"``

Returns:

.. code-block:: json

  [
    {
      "id": "f3b7fc8498cf5a17",
      "created": "2021-03-05T15:25:24.331000Z",
      "properties": {
        "pid": "deposit:f3b7fc8498cf5a17",
        "namespace": "deposit",
        "type": "Deposit"
      },
      "metadata": {
        "base": {
          "title": "Test API",
          "creator": [
            "Test creator",
            "Test unique"
          ]
        }
      },
      "links": {
        "self": "https://$SDR_HOST/api/objects/deposit/f3b7fc8498cf5a17"
      }
    },
    {
      "id": "50253b9ac1405e7e",
      "created": "2021-02-25T21:03:50.779000Z",
      "properties": {
        "pid": "deposit:50253b9ac1405e7e",
        "namespace": "deposit",
        "type": "Deposit"
      },
      "metadata": {
        "base": {
          "title": "Test closed API update",
          "creator": [
            "Test"
          ]
        }
      },
      "links": {
        "self": "https://$SDR_HOST/api/objects/deposit/50253b9ac1405e7e"
      }
    }
  ]


.. _rest-api-ref-list-all-community-collections:

List all community collections
______________________

List all collections of a community.

- HTTP method: ``GET``

- URL path: ``/api/objects/community/COMMUNITY_ID/collections``

- Required parameters: None

- Status code on success: ``200``

- Returns: the list of communities (in JSON format) or an error message.

Command:

``curl "https://$SDR_HOST/api/objects/community/$COMMUNITY_ID/collections"``

Returns:

.. code-block:: json

  [
    {
      "id": "e4cbd982d2426eba",
      "created": "2020-10-06T12:58:15.058000Z",
      "properties": {
        "pid": "collection:e4cbd982d2426eba",
        "namespace": "collection",
        "type": "Collection"
      },
      "metadata": {
        "base": {
          "title": "Test admin",
          "creator": [
            "Admin"
          ]
        }
      },
      "links": {
        "self": "https://$SDR_HOST/api/objects/collection/e4cbd982d2426eba"
      }
    },
    {
      "id": "a18755837dd9c65c",
      "created": "2020-10-07T12:13:26.258000Z",
      "properties": {
        "pid": "collection:a18755837dd9c65c",
        "namespace": "collection",
        "type": "Collection"
      },
      "metadata": {
        "base": {
          "title": "Test collection 114",
          "creator": [
            "Test",
            "Test 3",
            "Test123"
          ]
        }
      },
      "links": {
        "self": "https://$SDR_HOST/api/objects/collection/a18755837dd9c65c"
      }
    },
    {
      "id": "cc99ce5f61719f0b",
      "created": "2021-02-01T21:09:10.076000Z",
      "properties": {
        "pid": "collection:cc99ce5f61719f0b",
        "namespace": "collection",
        "type": "Collection"
      },
      "metadata": {
        "base": {
          "title": "Test no DOI policy",
          "creator": [
            "Test"
          ]
        }
      },
      "links": {
        "self": "https://$SDR_HOST/api/objects/collection/cc99ce5f61719f0b"
      }
    }
  ]

.. _rest-api-ref-get-community-schema:

Get community schema
______________________

Retrieves the JSON schema of deposits approved by a specific community.

- HTTP method: ``GET``

- URL path: ``/api/objects/community/COMMUNITY_ID/schema``

- Required parameters: None

- Status code on success: ``200``

- Returns: the community metadata schema, embedded in a JSON object, or an error message.

Command:

``curl "https://$SDR_HOST/api/objects/community/COMMUNITY_ID/schema"``

Returns:

.. code-block:: json

  {
    "$schema": "https://$SDR_HOST/static/schemas/object-metadata",
    "id": "astrophysics",
    "created": "2019-07-23T09:57:53.528000Z",
    "updated": "2020-10-05T19:17:43.031000Z",
    "properties": {
      "namespace": "schema",
      "pid": "schema:astrophysics",
      "epicpid": "21.T12996/0B6983E7-F185-449A-97EE-F63BED651ED0",
      "doi": "10.21945/SURF-image.8ff2ae03-c9cac144",
      "type": "schema",
      "state": "published",
      "sharelevel": "open public access",
      "owner": "user:1"
    },
    "fields": [
      {
        "index": "0",
        "name": "datatype",
        "type": "xs:normalizedString",
        "use": "M",
        "label": "Data type",
        "desc": "The type of data in the dataset",
        "useString": "Mandatory"
      },
      {
        "index": "1",
        "name": "study",
        "type": "vocabulary",
        "use": "M",
        "label": "Study type",
        "desc": "Astrophysical study type",
        "useString": "Mandatory"
      },
      {
        "index": "2",
        "name": "simulation",
        "type": "vocabulary",
        "use": "M",
        "label": "Simulation type",
        "desc": "Type of simulation",
        "useString": "Mandatory"
      }
    ],
    "links": {
      "self": "https://$SDR_HOST/api/objects/schema/astrophysics",
      "landing": "https://$SDR_HOST/schema/astrophysics",
      "relationships": {
        "schema": "https://$SDR_HOST"
      }
    },
    "metadata": {
      "base": {
        "$schema": "https://$SDR_HOST/api/objects/schema/dublin",
        "title": "Astrophysics metadata schema",
        "identifier": [
          "schema:astrophysics",
          "epic:21.T12996/0B6983E7-F185-449A-97EE-F63BED651ED0",
          "hdl:21.T12996/0B6983E7-F185-449A-97EE-F63BED651ED0"
        ],
        "rights": [
          "info:eu-repo/semantics/openAccess"
        ]
      }
    }
  }

.. _rest-api-ref-list-all-objects:

List all objects
______________________

List all the objects, without any filtering.

- HTTP method: ``GET``

- URL path: ``/api/objects``

- Required parameters: None

- Optional parameters: ``page``, ``size``, ``type``

- Status code on success: ``200``

- Returns: the list of objects (in JSON format) or an error message.

Command:

``curl "https://$SDR_HOST/api/objects"``

Returns:

.. code-block:: json

  {
    "params": {
      "query": "*",
      "type": "",
      "page": 1,
      "size": 25,
      "start": 1,
      "end": 25,
      "pages": 33
    },
    "hits": {
      "hits": [
        {
          "pid": "category:agricultural",
          "title": "Agricultural Sciences",
          "description": "This is the Agricultural Sciences category",
          "createdDate": "2019-03-28T09:53:27.919000Z",
          "state": "Published",
          "url": "https://$SDR_HOST/category/agricultural",
          "type": "Category"
        },
        ...
        {
          "pid": "collection:cosmogrid-2048",
          "title": "The Cosmogrid Simulation: Statistical Properties of Small Dark Matter Halos 2048³ resolution",
          "description": "...",
          "createdDate": "2020-04-22T19:41:21.212000Z",
          "state": "Published",
          "url": "https://$SDR_HOST/collection/cosmogrid-2048",
          "type": "Collection"
        },
        {
          "pid": "collection:cosmogrid-512",
          "title": "The Cosmogrid Simulation: Statistical Properties of Small Dark Matter Halos 512³ resolution",
          "description": "...",
          "createdDate": "2020-04-22T19:40:38.620000Z",
          "state": "Published",
          "url": "https://$SDR_HOST/collection/cosmogrid-512",
          "type": "Collection"
        }
      ],
      "total": 819
    },
    "links": {
      "self": "https://$SDR_HOST/api/objects?",
      "next": "https://$SDR_HOST/api/objects?page=2",
      "first": "https://$SDR_HOST/api/objects?page=1",
      "last": "https://$SDR_HOST/api/objects?page=33"
    }
  }


.. _rest-api-ref-search-objects:

Search objects
______________________

Search all the published objects for a query string.

- HTTP method: ``GET``

- URL path: ``/api/objects``

- Required parameters: none

- Optional parameters: ``query``, ``page``, ``size``, ``sort``, ``context``, ``type``

- Status code on success: ``200``

- Returns: the list of matching deposits (in JSON format) or an error message

- Notes:

 - The parameter ``query`` determines the keywords to search for, separated by a space.

 -     If a field name is prepended followed by a colon and the search value, the search is limited to that field, e.g. 'creators.creator:user' searches for deposits with a 'user' in the creator metadata field.

 -     If the parameter q is omitted, all deposits are returned (in paginated form). See also :ref:`List all deposits <rest-api-ref-list-all-objects>`.

 -     For a better understanding of search queries, a listing of available search fields and advanced options like operators, please refer to the Data Repository Advanced Search documentation on how to create them.

 - Using the page and size parameter, pagination can be established by providing integer values for these parameters. The page parameter is 1-based.

 -     For example: using a value of 2 for page and 50 for size will return the deposits from number 51 to 100 (if there are at least 100 deposits available on the instance)

 - The sort parameter can be either ``asc`` or ``desc``.

Command:

``curl "https://$SDR_HOST/api/objects/?query=$QUERY_STRING&page=1&size=100&sort=desc"``

.. _rest-api-ref-search-drafts:

Search drafts
______________________

List all your draft objects.

- HTTP method: ``GET``

- URL path: ``/api/objects``

- Required parameters: ``token``, ``drafts``

- Optional parameters: ``query``, ``type``

- Status code on success: ``200``

- Returns: the list of matching drafts (in JSON format) or an error message.

- Notes:

 - You can only list your own draft objects.

 - You can add search parameters to narrow down your search, see :ref:`Search objects <rest-api-ref-search-objects>`.

Command:

``curl "https://$SDR_HOST/api/objects/?drafts&token=$TOKEN"``

.. _rest-api-ref-get-specific-deposit:

Get specific deposit
______________________

List the metadata of the deposit specified by ``NAMESPACE`` and ``DEPOSIT_ID``. The metadata of all deposits are always public.

- HTTP method: ``GET``

- URL path: ``/api/objects/NAMESPACE/DEPOSIT_ID``

- Optional parameters: ``token``

- Status code on success: ``200``

- Notes: the access token is only required when a deposit is in draft state.

Command:

``curl "https://$SDR_HOST/api/objects/deposit/c800a32839fa47d9"``

.. _rest-api-ref-get-specific-collection:

Get specific collection
______________________

List the metadata of the collection specified by ``COLLECTION_ID``. The metadata of all collections are always public.

- HTTP method: ``GET``

- URL path: ``/api/objects/collection/COLLECTION_ID``

- Optional parameters: ``token``

- Status code on success: ``200``

- Notes: the access token is only required when a collection is not publicly available.

Command:

``curl "https://$SDR_HOST/api/objects/collection/$COLLECTION_ID"``

.. _rest-api-ref-deposit-administration:

=============
Object administration
=============

The following requests concern the creation, update and management of objects.

.. _rest-api-ref-create-draft-deposit:

Create draft deposit
______________________

Create a new deposit, in the draft state.

- HTTP method: ``POST``

- URL path: ``/api/objects/deposit``

- Required parameters: ``token``

- Payload data: JSON object with basic metadata of the object, at least the required fields of the basic metadata schema of each new deposit: titles, community and open_access.

- Status code on success: ``201``

- Returns: the new draft deposit metadata including new URL of the object.

- Notes: you cannot change the community the deposit resides in after you have created the deposit.

Example 1
-----------

The following example creates an open-access deposit for a community with identifier ``community:surf`` with title 'My dataset deposit'. Any other metadata fields cannot be provided here.

Command:

``curl -X POST -H "Content-Type:application/json"
  -d '{"title":"My dataset deposit", "community":"community:surf", "sharelevel": "Open"}' "https://$SDR_HOST/api/objects/deposit?token=$TOKEN"``

Payload:

.. code-block:: json

  {
    "title": "My dataset deposit",
    "community": "community:surf",
    "sharelevel": "Open",
  }

Returns:

.. code-block:: json

  {
    "$schema": "https://$SDR_HOST/static/schemas/object-metadata",
    "id": "bd387af9afe48d0a",
    "created": "2021-03-10T20:05:43.250000Z",
    "updated": "2021-03-10T20:05:43.250000Z",
    "properties": {
      "namespace": "deposit",
      "pid": "deposit:bd387af9afe48d0a",
      "type": "deposit",
      "state": "draft",
      "sharelevel": "open public access",
      "owner": "user:86"
    },
    "links": {
      "self": "https://$SDR_HOST/api/objects/deposit/bd387af9afe48d0a",
      "landing": "https://$SDR_HOST/deposit/bd387af9afe48d0a",
      "relationships": {
        "community": "https://$SDR_HOST/api/objects/community/surf",
        "schema": "https://$SDR_HOST"
      }
    },
    "metadata": {
      "base": {
        "$schema": "https://$SDR_HOST/api/objects/schema/dublin",
        "title": "My dataset deposit",
        "identifier": "deposit:bd387af9afe48d0a",
        "rights": [
          "info:eu-repo/semantics/openAccess"
        ]
      }
    }
  }


.. _rest-api-ref-common-errors:

Common errors
-------------

On metadata validation error when an incorrect share level is given:

.. code-block:: json

  {
    "error": "Invalid share level 'O', choose from 'Open', 'Restricted', 'Closed'"
  }

On metadata validation error when a required field is missing:

.. code-block:: json

  {
    "error": "Missing mandatory fields: 'title'"
  }

.. _rest-api-ref-upload-file-into-draft-deposit:

Upload file into draft deposit
______________________

To upload a new file into a draft deposit object, first you need to identify the file bucket URL. This URL can be found in the information returned when querying a draft deposit, in the 'links/files' section of the returned data.

- HTTP method: ``PUT``

- URL path: ``/api/object/NAMESPACE/DEPOSIT_ID/files/FILE_NAME``

- Required parameters: ``token``

- Payload data: the file, sent as direct stream, for curl use the --data-binary @FILE_NAME option for this.

- Status code on success: ``200``

- Returns: informations about the newly uploaded file

- Notes:

 - Using the ``--data-binary`` option will load the entire file into memory before being sent to Data Repository

 - For large files instead use the ``-T`` option followed by the file name (without a ``@`` sign)

 - Also, to avoid timeouts please use the ``-H "Transfer-Encoding: chunked"`` option and value to send a file in chunks instead of all at once.

Command:

``curl -X PUT -H 'Accept:application/json' -H 'Content-Type:application/octet-stream' --data-binary @$FILE_NAME "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID/files/$FILE_NAME?token=$TOKEN"``

Command:

``curl -X PUT -H 'Accept:application/json' -H 'Content-Type:application/octet-stream' -H 'Transfer-Encoding:chunked' -T $FILE_NAME "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID/files/$FILE_NAME?token=$TOKEN"``

Returns:

.. code-block:: json

  {
    "$schema": "https://$SDR_HOST/static/schemas/object-metadata",
    "id": "bd387af9afe48d0a",
    "created": "2021-03-10T20:05:43.250000Z",
    "updated": "2021-03-10T20:09:30.379000Z",
    "properties": {
      "namespace": "deposit",
      "pid": "deposit:bd387af9afe48d0a",
      "type": "deposit",
      "state": "draft",
      "sharelevel": "open public access",
      "owner": "user:86"
    },
    "files": [
      {
        "name": "$FILE_NAME",
        "url": "https://$SDR_HOST/deposit/bd387af9afe48d0a/files/$FILE_NAME",
        "external": false,
        "size": 691,
        "mimetype": "text/plain",
        "md5": "",
        "epicpid": "21.T12996/5ddde41c-a461-a861-45fd-76594f2b5a20"
      }
    ],
    "links": {
      "self": "https://$SDR_HOST/api/objects/deposit/bd387af9afe48d0a",
      "landing": "https://$SDR_HOST/deposit/bd387af9afe48d0a",
      "relationships": {
        "community": "https://$SDR_HOST/api/objects/community/surf",
        "schema": "https://$SDR_HOST"
      },
      "files": "https://$SDR_HOST/api/objects/deposit/bd387af9afe48d0a/files"
    },
    "metadata": {
      "base": {
        "$schema": "https://$SDR_HOST/api/objects/schema/dublin",
        "title": "My dataset deposit",
        "identifier": "deposit:bd387af9afe48d0a",
        "rights": [
          "info:eu-repo/semantics/openAccess"
        ]
      }
    }
  }


.. _rest-api-ref-delete-file-from-draft-deposit:

Delete file from draft deposit
______________________

Send a DELETE request to the file's URL, which is the same URL used for uploading.

- HTTP method: ``DELETE``

- URL path: ``/api/objects/NAMESPACE/DEPOSIT_ID/files/FILE_NAME``

- Required parameters: ``token``

- Status code on success: ``204``

- Returns: no content

Command:

``curl -X DELETE "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID/files/$FILE_NAME?token=$TOKEN"``


.. _rest-api-ref-list-files-of-deposit:

List files of deposit
______________________

List the files uploaded into a deposit object.

- HTTP method: ``GET``

- URL path: ``/api/objects/NAMESPACE/OBJECT_ID/files``

- Required parameters: ``token``

- Status code on success: ``200``

- Returns: information about all the files in the deposit object

- Notes: the access token is only required if the deposit is in draft state.

Command:

``curl "https://$SDR_HOST/api/objects/$NAMESPACE/$OBJECT_ID/files?token=$TOKEN"``

Returns:

.. code-block:: json

  [
    {
      "name": "data.txt",
      "url": "https://$SDR_HOST/deposit/f3b7fc8498cf5a17/files/data.txt",
      "external": false,
      "size": 691,
      "mimetype": "text/plain",
      "md5": "341fb1bc1d92d82d1a79d9f4d80f649b",
      "epicpid": "21.T12996/ec16cef9-ff29-a39e-45da-40e1338fc4c3"
    },
    {
      "name": "data2.txt",
      "url": "https://$SDR_HOST/deposit/f3b7fc8498cf5a17/files/data2.txt",
      "external": false,
      "size": 691,
      "mimetype": "text/plain",
      "md5": "341fb1bc1d92d82d1a79d9f4d80f649b",
      "epicpid": "21.T12996/db9d92a9-bde1-bc96-432f-1fc65b8c2f0e"
    },
    {
      "name": "data2.txt2",
      "url": "https://$SDR_HOST/deposit/f3b7fc8498cf5a17/files/data2.txt2",
      "external": false,
      "size": 691,
      "mimetype": "text/plain",
      "md5": "341fb1bc1d92d82d1a79d9f4d80f649b",
      "epicpid": "21.T12996/59239fbb-9238-b975-49c4-4187feed59b2"
    }
  ]

.. _rest-api-ref-update-draft-deposit-metadata:

Update draft deposit metadata
______________________

This action updates the draft deposit with new information.

- HTTP method: ``PATCH``

- URL path: ``/api/objects/NAMESPACE/OBJECT_ID``

- Required parameters: ``token``

- Payload data: the metadata for the draft deposit to be updated, in the JSON Patch format (see http://jsonpatch.com/)

- Status code on success: ``200``

- Returns: the updated metadata of the draft deposit.

- Notes: The JSON Patch format contains one or more JSONPath strings. The root of these paths are the metadata object, as this is the only mutable object. For instance, to update the title field of the deposit, use this JSONPath: '/title'. To update a field in a community or collection metadata schema, use the '/community/<field>' or '/collection/<field>' paths respectively.

Example 1
-----------

The following example adds two values to the metadata field `keywords` of an existing draft deposit.

Command:

``curl -X PATCH -H 'Content-Type:application/json-patch+json' -d '[{"op": "add", "path":"/creator", "value": ["Creator #1"]}]' "https://$SDR_HOST/api/objects/$NAMESPACE/$OBJECT_ID?token=$TOKEN"``

Returns:

.. code-block:: json

  {
    "$schema": "https://$SDR_HOST/static/schemas/object-metadata",
    "id": "bd387af9afe48d0a",
    "created": "2021-03-10T20:05:43.250000Z",
    "updated": "2021-03-10T20:12:15.939000Z",
    "properties": {
      "namespace": "deposit",
      "pid": "deposit:bd387af9afe48d0a",
      "type": "deposit",
      "state": "draft",
      "sharelevel": "open public access",
      "owner": "user:86"
    },
    "links": {
      "self": "https://$SDR_HOST/api/objects/deposit/bd387af9afe48d0a",
      "landing": "https://$SDR_HOST/deposit/bd387af9afe48d0a",
      "relationships": {
        "community": "https://$SDR_HOST/api/objects/community/surf",
        "schema": "https://$SDR_HOST"
      }
    },
    "metadata": {
      "base": {
        "$schema": "https://$SDR_HOST/api/objects/schema/dublin",
        "title": "My data deposit",
        "identifier": "deposit:bd387af9afe48d0a",
        "creator": [
          "Creator #1"
        ],
        "rights": [
          "info:eu-repo/semantics/openAccess"
        ]
      }
    }
  }

Example 2
-----------

This example replaces the value of the title of a deposit. This requires a JSONPath ``/title`` with operation ``replace`` as we are updating an existing value of a multivalued field.

Command:

``curl -X PATCH -H 'Content-Type:application/json-patch+json' -d '[{"op": "replace", "path":"/title", "value": ["New title"]}]' "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID?token=$TOKEN"``

Returns:

.. code-block:: json

  {
    "$schema": "https://$SDR_HOST/static/schemas/object-metadata",
    "id": "bd387af9afe48d0a",
    "created": "2021-03-10T20:05:43.250000Z",
    "updated": "2021-03-10T20:14:11.996000Z",
    "properties": {
      "namespace": "deposit",
      "pid": "deposit:bd387af9afe48d0a",
      "type": "deposit",
      "state": "draft",
      "sharelevel": "open public access",
      "owner": "user:86"
    },
    "links": {
      "self": "https://$SDR_HOST/api/objects/deposit/bd387af9afe48d0a",
      "landing": "https://$SDR_HOST/deposit/bd387af9afe48d0a",
      "relationships": {
        "community": "https://$SDR_HOST/api/objects/community/surf",
        "schema": "https://$SDR_HOST"
      }
    },
    "metadata": {
      "base": {
        "$schema": "https://$SDR_HOST/api/objects/schema/dublin",
        "title": "New title",
        "identifier": "deposit:bd387af9afe48d0a",
        "creator": [
          "Creator #1"
        ],
        "rights": [
          "info:eu-repo/semantics/openAccess"
        ]
      }
    }
  }

Example 3
-----------

The next example updates the community-specific metadata fields ``field_1`` and ``field_2`` of an existing draft deposit of community with identifier ``community:surf``. Note that in order to update a community-specific field, the JSONPath `/community/FIELD_NAME` is required.

Command:

``curl -X POST -H "Content-Type:application/json-patch+json" -d '[{"op": "add", "path": "/community/field_1", "value": "value_1"}, {"op": "add", "path": "/community/field_2", "value": "value_2"}]' "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID?token=$TOKEN"``

Returns:

.. code-block:: json

  {
    "$schema": "https://$SDR_HOST/static/schemas/object-metadata",
    "id": "bd387af9afe48d0a",
    "created": "2021-03-10T20:05:43.250000Z",
    "updated": "2021-03-10T20:14:11.996000Z",
    "properties": {
      "namespace": "deposit",
      "pid": "deposit:bd387af9afe48d0a",
      "type": "deposit",
      "state": "draft",
      "sharelevel": "open public access",
      "owner": "user:86"
    },
    "links": {
      "self": "https://$SDR_HOST/api/objects/deposit/bd387af9afe48d0a",
      "landing": "https://$SDR_HOST/deposit/bd387af9afe48d0a",
      "relationships": {
        "community": "https://$SDR_HOST/api/objects/community/surf",
        "schema": "https://$SDR_HOST"
      }
    },
    "metadata": {
      "base": {
        "$schema": "https://$SDR_HOST/api/objects/schema/dublin",
        "title": "New title",
        "identifier": "deposit:bd387af9afe48d0a",
        "creator": [
          "Creator #1"
        ],
        "rights": [
          "info:eu-repo/semantics/openAccess"
        ]
      },
      "community": {
        "field_1": "value_1",
        "field_2": "value_2"
      }
    }
  }


Common errors
-------------

On JSON Patch operation error:

.. code-block:: json

TBD

One of the JSON Patch operations is invalid.

On JSON Patch content type error:

.. code-block:: json

TBD


The supplied content type header value is invalid.

On metadata validation error:

.. code-block:: json

TBD

The supplied value for the metadata field is invalid.

.. _rest-api-ref-add-externally-referenced-files-to-draft-deposit:

Add externally referenced files to draft deposit
______________________

To add files that are located outside of Data Repository, a reference to that file can be added to a draft deposit object by defining a list of external references that include a file name and the corresponding EPIC PID. External references are added as normal metadata using a JSON Patch and can only be added during the draft stage.

- HTTP method: ``PATCH``

- URL path: ``/api/objects/NAMESPACE/DEPOSIT_ID/files``

- Required parameters: ``token``

- Payload data: the list of external references provided as JSON.

- Status code on success: ``200``

- Returns: informations about the updated metadata of the draft deposit

- Notes: you must provide the external references using EPIC PIDs and therefore you need to be able to register new PIDs with an EPIC PID hosting institute using a registered prefix. It is possible to get a prefix through SURF, send an email through helpdesk@surfsara.nl or use the service desk.

Command:

``curl -X PATCH -H 'Accept:application/json-patch+json' -d '' "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID/files?token=$TOKEN"``

.. _rest-api-ref-submit-draft-deposit-for-publication:

Submit draft deposit for publication
______________________

This action marks the draft deposit as complete and submits it for publication. Please be advised that publishing the draft will make its files immutable.

Depending on the community and collection attached metadata schemas, specific metadata fields could be required in order to successfully publish a deposit. In case one of the required fields is missing the request fails and an error message is returned with further details.

- HTTP method: ``POST``

- URL path: ``/api/objects/NAMESPACE/DEPOSIT_ID/submit``

- Required parameters: ``token``

- Payload data: None

- Status code on success: ``200``

- Notes: this request is essentially a metadata update request as described above.

Command:

``curl -X POST "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID/submit?token=$TOKEN"``

Returns:

.. code-block:: json

  {
    "$schema": "https://$SDR_HOST/static/schemas/object-metadata",
    "id": "f3b7fc8498cf5a17",
    "created": "2021-03-05T15:25:24.331000Z",
    "updated": "2021-03-05T17:21:57.448000Z",
    "properties": {
      "namespace": "deposit",
      "pid": "deposit:f3b7fc8498cf5a17",
      "epicpid": "21.T12996/1dd4137e-e262-83db-4f10-a27054c41fa6",
      "doi": "10.21945/SURF-image.1f9b3206-f3b7fc8498cf5a17",
      "type": "deposit",
      "state": "published",
      "sharelevel": "open public access",
      "owner": "user:86"
    },
    "files": [
      {
        "name": "data.txt",
        "url": "https://$SDR_HOST/deposit/f3b7fc8498cf5a17/files/data.txt",
        "external": false,
        "size": 691,
        "mimetype": "text/plain",
        "md5": "341fb1bc1d92d82d1a79d9f4d80f649b",
        "epicpid": "21.T12996/ec16cef9-ff29-a39e-45da-40e1338fc4c3"
      },
      {
        "name": "data2.txt",
        "url": "https://$SDR_HOST/deposit/f3b7fc8498cf5a17/files/data2.txt",
        "external": false,
        "size": 691,
        "mimetype": "text/plain",
        "md5": "341fb1bc1d92d82d1a79d9f4d80f649b",
        "epicpid": "21.T12996/db9d92a9-bde1-bc96-432f-1fc65b8c2f0e"
      },
      {
        "name": "data3.txt",
        "url": "https://$SDR_HOST/deposit/f3b7fc8498cf5a17/files/data2.txt2",
        "external": false,
        "size": 691,
        "mimetype": "text/plain",
        "md5": "341fb1bc1d92d82d1a79d9f4d80f649b",
        "epicpid": "21.T12996/59239fbb-9238-b975-49c4-4187feed59b2"
      }
    ],
    "links": {
      "self": "https://$SDR_HOST/api/objects/deposit/f3b7fc8498cf5a17",
      "landing": "https://$SDR_HOST/deposit/f3b7fc8498cf5a17",
      "relationships": {
        "community": "https://$SDR_HOST/api/objects/community/surf",
        "schema": "https://$SDR_HOST"
      },
      "files": "https://$SDR_HOST/api/objects/deposit/f3b7fc8498cf5a17/files"
    },
    "metadata": {
      "base": {
        "$schema": "https://$SDR_HOST/api/objects/schema/dublin",
        "title": "Test API",
        "identifier": "deposit:f3b7fc8498cf5a17",
        "creator": [
          "Test creator",
          "Test unique"
        ],
        "description": "Test description",
        "type": "Dataset",
        "subject": [
          "Test",
          "REST API"
        ],
        "rights": [
          {
            "name": "Public Domain (PD)"
          },
          "info:eu-repo/semantics/openAccess"
        ],
        "date": "2021-01-01"
      }
    }
  }


.. _rest-api-ref-update-published-deposit-metadata:

Update published deposit metadata
______________________

This request updates the metadata of an already published deposit without creating a new version.

- HTTP method: ``PATCH``

- URL path: ``/api/objects/deposit/DEPOSIT_ID``

- Required parameters: ``token``

- Payload data: the metadata for the published deposit object to be updated, in the JSON Patch format (see http://jsonpatch.com/)

- Status code on success: ``200``

- Notes: The JSON Patch format contains one or more JSONPath strings. The root of these paths are the metadata object, as this is the only mutable object. For instance, to update the title field of the deposit, use this JSONPath: /titles/title

See the :ref:`Update draft deposit metadata <rest-api-ref-update-draft-deposit-metadata>` request for examples.


.. _rest-api-ref-other-requests:

===================
Other requests
===================

The following requests are the remaining requests possible in Data Repository. Click on a title to show details.

.. _rest-api-ref-delete-draft-object:

Delete draft object
______________________

Delete a draft object.

- HTTP method: ``DELETE``

- URL path: ``/api/objects/NAMESPACE/OBJECT_ID``

- Required parameters: ``token``

- Status code on success: ``204``

- Returns: no contents.

- Notes: you can only delete draft objects that you own, not published objects.

Command:

``curl -X DELETE "https://$SDR_HOST/api/objects/$NAMESPACE/$OBJECT_ID?token=$TOKEN"``


.. _rest-api-ref-delete-published-object:

Delete published object
______________________

Delete a published object, either a collection or deposit. This can only be done by a site administrator.

- HTTP method: ``DELETE``

- URL path: ``/api/objects/NAMESPACE/OBJECT_ID``

- Required parameters: ``token``

- Status code on success: ``204``

- Returns: no contents.

- Notes: only a site administrator can delete a published object.

Command:

``curl -X DELETE "https://$SDR_HOST/api/objects/NAMESPACE/$OBJECT_ID/?token=$TOKEN"``
