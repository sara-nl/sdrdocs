.. _rest-api-ref:

**************
REST API reference
**************

In this page all available REST API requests are listed, together with examples.

.. contents::
    :depth: 4

.. _rest-api-ref-structure:

Structure
______________________

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

=============
Object retrieval
==============

The following requests concern the retrieval of information about deposits and communities. Click on a title to show details.

.. _rest-api-ref-list-all-communities:

List all communities
______________________

List all the communities, without any filtering.

- HTTP method: ``GET``

- URL path: ``/api/objects/community``

- Required parameters: None

- Status code on success: ``200``

- Returns: the list of communities (in JSON format) or an error message.

Command:

``curl "https://$SDR_HOST/api/objects/community"``

Returns:

.. code-block:: json

  {
    "hits": {
      "hits": [
        {
          "created": "Tue, 18 Oct 2016 08:30:47 GMT",
          "description": "The big Eudat community. Use this community if no other is suited for you",
          "id": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
          "links": {
            "self": "https://trng-repository.surfsara.nl/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095"
          },
          "logo": "/img/communities/eudat.png",
          "name": "EUDAT",
          "updated": "Tue, 18 Oct 2016 08:30:47 GMT"
        },
        ...
      ],
      "total": 11
    },
    "links": {
      "self": "https://trng-repository.surfsara.nl/api/communities/"
    }
  }

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

  {
    "hits": {
      "hits": [
        {
          "created": "Tue, 18 Oct 2016 08:30:47 GMT",
          "description": "The big Eudat community. Use this community if no other is suited for you",
          "id": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
          "links": {
            "self": "https://trng-repository.surfsara.nl/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095"
          },
          "logo": "/img/communities/eudat.png",
          "name": "EUDAT",
          "updated": "Tue, 18 Oct 2016 08:30:47 GMT"
        },
        ...
      ],
      "total": 11
    },
    "links": {
      "self": "https://trng-repository.surfsara.nl/api/communities/"
    }
  }

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
    "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
    "draft_json_schema": {
      "$ref": "https://trng-repository.surfsara.nl/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095/schemas/0#/json_schema",
      "$schema": "http://json-schema.org/draft-04/schema#"
    },
    "json_schema": {
      "allOf": [
        ...
      ]
    },
    "links": {
      "self": "https://trng-repository.surfsara.nl/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095/schemas/0"
    },
    "version": 0
  }

.. _rest-api-ref-list-all-objects:

List all objects
______________________

List all the objects, without any filtering.

- HTTP method: ``GET``

- URL path: ``/api/objects``

- Required parameters: None

- Optional parameters: page, size, mostrecent

- Status code on success: ``200``

- Returns: the list of objects (in JSON format) or an error message.

Command:

``curl "https://$SDR_HOST/api/objects"``

Returns:

.. code-block:: json

  {
    "aggregations": {
      "type": {
        "buckets": [],
        "doc_count_error_upper_bound": 0,
        "sum_other_doc_count": 0
      }
    },
    "hits": {
      "hits": [
        {
          "created": "2016-10-19T11:32:46.095143+00:00",
          "files": [
            {
              "bucket": "473086fc-e125-4389-8483-b8a4f130e181",
              "checksum": "md5:c8afdb36c52cf4727836669019e69222",
              "key": "myfile",
              "size": 9,
              "version_id": "324fdf1d-0005-41b1-a9c5-26a8eabd05a2"
            }
          ],
          "id": "a1c2ef96a1e446fa9bd7a2a46d2242d4",
          "links": {
            "files": "https://trng-repository.surfsara.nl/api/files/473086fc-e125-4389-8483-b8a4f130e181",
            "self": "https://trng-repository.surfsara.nl/api/objects/a1c2ef96a1e446fa9bd7a2a46d2242d4"
          },
          "metadata": {
            ...: ...
          },
          "updated": "2016-10-19T11:32:46.095152+00:00"
        },
        ...
      ],
      "total": 51
    },
    "links": {
      "next": "https://trng-repository.surfsara.nl/api/objects/?sort=mostrecent&q=&page=2",
      "self": "https://trng-repository.surfsara.nl/api/objects/?sort=mostrecent&q=&page=1"
    }
  }

.. _rest-api-ref-list-deposits-per-community:

List deposits per community
______________________

List all deposits of a specific community.

- HTTP method: ``GET``

- URL path: ``/api/objects``

- Required parameters: ``context`` with value ``community:COMMUNITY_ID``

- Status code on success: ``200``

- Returns: the list of deposits (in JSON format) or an error message

- Notes: you can use search parameters to further narrow your search as described in the 'Search deposits' section.

Command:

``curl "https://$SDR_HOST/api/objects/?context=community:$COMMUNITY_ID"``

Returns:

.. code-block:: json

  {
    "aggregations": {
      "type": {
        "buckets": [],
        "doc_count_error_upper_bound": 0,
        "sum_other_doc_count": 0
      }
    },
    "hits": {
      "hits": [
        {
          "created": "2016-10-24T11:29:27.016892+00:00",
          "id": "f7fddf6f111f4362a9e4661294e2b59e",
          "links": {
            "files": "https://trng-repository.surfsara.nl/api/files/90ea3483-2792-4483-9392-7d624b610398",
            "self": "https://trng-repository.surfsara.nl/api/objects/f7fddf6f111f4362a9e4661294e2b59e",
            "versions": "https://trng-repository.surfsara.nl/api/objects/d855e187e3864ddcaa1b68625866dd78/versions"
          },
          "updated": "2016-10-24T11:29:27.016900+00:00",
          ...: ...
        },
        ...
      ],
      "total": 32
    },
    "links": {
      "next": "https://trng-repository.surfsara.nl/api/objects/?sort=bestmatch&q=community%3Ae9b9792e-79fb-4b07-b6b4-b9c2bd06d095&size=10&page=2",
      "self": "https://trng-repository.surfsara.nl/api/objects/?sort=bestmatch&q=community%3Ae9b9792e-79fb-4b07-b6b4-b9c2bd06d095&size=10&page=1"
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

- Required parameters: token

- Status code on success: ``200``

- Notes: the access token is only required when a deposit is not publicly available.

Command:

``curl "https://$SDR_HOST/api/objects/deposit/c800a32839fa47d9"``

.. _rest-api-ref-get-specific-collection:

Get specific collection
______________________

List the metadata of the collection specified by ``COLLECTION_ID``. The metadata of all collections are always public.

- HTTP method: ``GET``

- URL path: ``/api/objects/NAMESPACE/COLLECTION_ID``

- Optional parameters: token

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

- Required parameters: token

- Payload data: JSON object with basic metadata of the object, at least the required fields of the basic metadata schema of each new deposit: titles, community and open_access.

- Status code on success: ``201``

- Returns: the new draft deposit metadata including new URL location. Please note that the returned JSON object contains also the URL of the file bucket used for the deposit. Also note that the URL of the draft deposit, needed for setting deposit metadata, will end in '/draft/'

- Notes: you cannot change the community the deposit resides in after you have created the deposit.

Example 1
-----------

The following example creates an open-access deposit for a community with identifier e9b9792e-79fb-4b07-b6b4-b9c2bd06d095 with title 'My dataset deposit', creators 'John Smith' and 'Jane Smith' and description of type abstract 'A simple description'.

Command:

``curl -X POST -H "Content-Type:application/json" -d '{"title":"My dataset deposit"}], "creators":[{"creator_name": "John Smith"}, {"creator_name": "Jane Smith"}], "descriptions":[{"description": "A simple description", "description_type": "Abstract"}], "community":"e9b9792e-79fb-4b07-b6b4-b9c2bd06d095", "open_access":true}' "https://$SDR_HOST/api/objects/?token=$TOKEN"``

Payload:

.. code-block:: json

  {
    "titles": [
      {
        "title": "My dataset deposit"
      }
    ],
    "creators": [
      {
        "creator_name": "John Smith"
      },
      {
        "creator_name": "Jane Smith"
      }
    ],
    "descriptions": [
      {
        "description": "A simple description",
        "description_type": "Abstract"
      }
    ],
    "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
    "open_access": true,
  }

Returns:

.. code-block:: json

  {
    "created": "2016-10-24T12:21:21.697737+00:00",
    "id": "01826ff3e4974415afdb2574a7ea5a91",
    "links": {
      "files": "https://trng-repository.surfsara.nl/api/files/5594a1bf-1484-4a01-b7d3-f1eb3d2e1dc6",
      "publication": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91",
      "self": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91/draft",
      "versions": "https://trng-repository.surfsara.nl/api/objects/d855e187e3864ddcaa1b68625866dd78/versions"
    },
    "metadata": {
      "$schema": "https://trng-repository.surfsara.nl/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095/schemas/0#/draft_json_schema",
      "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
      "community_specific": {
        "field_1": "value_1",
        "field_2": "value_2"
      },
      "open_access": true,
      "owners": [
        8
      ],
      "publication_state": "draft",
      "titles": [
        {
          "title": "My dataset deposit"
        }
      ],
      "creators": [
        {
          "creator_name": "John Smith"
        },
        {
          "creator_name": "Jane Smith"
        }
      ]
    },
    "updated": "2016-10-24T12:21:21.697744+00:00"
  }

Example 2
-----------

The next example creates an open-access deposit for a community with identifier 94a9567e-2fba-4677-8fde-a8b68bdb63e8 with title 'My community deposit', creator 'John Smith'. The following community-specific fields are added: 'field_1' and 'field_2'.

For this to work, the schema identifier of the community metadata schema is required. You can get this information from the community metadata using the Get community schema request, although it is a bit hidden. The correct JSONPath for this metadata is /json_schema/allOf/1/properties/community_specific/required, in this example 5108aff5-be5b-4d92-968a-22930ee65e94.

Command:

``curl -X POST -H "Content-Type:application/json" -d '{"titles":[{"title":"My community deposit"}], "creators":[{"creator_name": "John Smith"}], "community":"94a9567e-2fba-4677-8fde-a8b68bdb63e8", "open_access":true, "community_specific": {"5108aff5-be5b-4d92-968a-22930ee65e94": {"field_1": "value", "field_2": "value"}}}' "https://$SDR_HOST/api/objects/?token=$TOKEN"``

Payload:

.. code-block:: json

  {
    "titles": [
      {
        "title": "My community deposit"
      }
    ],
    "creators": [
      {
        "creator_name": "John Smith"
      }
    ],
    "community": "94a9567e-2fba-4677-8fde-a8b68bdb63e8",
    "open_access": true,
    "community_specific": {
      "5108aff5-be5b-4d92-968a-22930ee65e94": {
        "field_1": "value",
        "field_2": "value"
      }
    }
  }

Returns:

.. code-block:: json

  {
    "created": "2016-10-24T12:21:21.697737+00:00",
    "id": "01826ff3e4974415afdb2574a7ea5a91",
    "links": {
      "files": "https://trng-repository.surfsara.nl/api/files/5594a1bf-1484-4a01-b7d3-f1eb3d2e1dc6",
      "publication": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91",
      "self": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91/draft",
      "versions": "https://trng-repository.surfsara.nl/api/objects/d855e187e3864ddcaa1b68625866dd78/versions"
    },
    "metadata": {
      "$schema": "https://trng-repository.surfsara.nl/api/communities/94a9567e-2fba-4677-8fde-a8b68bdb63e8/schemas/0#/draft_json_schema",
      "community": "94a9567e-2fba-4677-8fde-a8b68bdb63e8",
      "community_specific": {
        "5108aff5-be5b-4d92-968a-22930ee65e94": {
          "field_1": "value_1",
          "field_2": "value_2"
        }
      },
      "open_access": true,
      "owners": [
        8
      ],
      "publication_state": "draft",
      "titles": [
        {
          "title": "My community deposit"
        }
      ],
      "creators": [
        {
          "creator_name": "John Smith"
        },
        {
          "creator_name": "Jane Smith"
        }
      ]
    },
    "updated": "2016-10-24T12:21:21.697744+00:00"
  }

.. _rest-api-ref-common-errors:

Common errors
-------------

On metadata validation error:

.. code-block:: json

  {
    "message": "Validation error.",
    "status": 400
  }

The supplied metadata is invalid or incorrectly structured. This means that either a specified field does not exist in the metadata schema, or that one of the values for a given field is invalid.

.. _rest-api-ref-upload-file-into-draft-deposit:

Upload file into draft deposit
______________________

To upload a new file into a draft deposit object, first you need to identify the file bucket URL. This URL can be found in the information returned when querying a draft deposit, in the 'links/files' section of the returned data.

- HTTP method: ``PUT``

- URL path: ``/api/files/FILE_BUCKET_ID/FILE_NAME``

- Required parameters: token

- Payload data: the file, sent as direct stream, for curl use the --data-binary @FILE_NAME option for this.

- Status code on success: ``200``

- Returns: informations about the newly uploaded file

- Notes:

 - Using the ``--data-binary`` option will load the entire file into memory before being sent to Data Repository

 - For large files instead use the ``-T`` option followed by the file name (without a ``@`` sign)

 - Also, to avoid timeouts please use the ``-H "Transfer-Encoding: chunked"`` option and value to send a file in chunks instead of all at once.

Command:

``curl -X PUT -H 'Accept:application/json' -H 'Content-Type:application/octet-stream' --data-binary @$FILE_NAME "https://$SDR_HOST/api/files/$FILE_BUCKET_ID/$FILE_NAME?token=$TOKEN"``

Command:

``curl -X PUT -H 'Accept:application/json' -H 'Content-Type:application/octet-stream' -H 'Transfer-Encoding:chunked' -T $FILE_NAME "https://$SDR_HOST/api/files/$FILE_BUCKET_ID/$FILE_NAME?token=$TOKEN"``

.. _rest-api-ref-delete-file-from-draft-deposit:

Delete file from draft deposit
______________________

Send a DELETE request to the file's URL, which is the same URL used for uploading.

- HTTP method: ``DELETE``

- URL path: ``/api/NAMESPACE/OBJECT_ID/files/FILE_NAME``

- Required parameters: token

- Status code on success: ``204``

- Returns: no content

Command:

``curl -X DELETE -H 'Accept:application/json' "https://$SDR_HOST/api/files/$FILE_BUCKET_ID/FileToBeRemoved.txt?token=$TOKEN"``

.. _rest-api-ref-list-files-of-deposit:

List files of deposit
______________________

List the files uploaded into a deposit object. For this request you need the FILE_BUCKET_ID which can be found in the metadata of the deposit. This does not include files that are referenced externally.

- HTTP method: ``GET``

- URL path: ``/api/objects/NAMESPACE/OBJECT_ID/files``

- Required parameters: token

- Status code on success: ``200``

- Returns: information about all the files in the deposit object

- Notes: the access token is only required if the deposit is in draft state.

Command:

``curl "https://$SDR_HOST/api/objects/NAMESPACE/OBJECT_ID/files?token=$TOKEN"``

.. _rest-api-ref-update-draft-deposit-metadata:

Update draft deposit metadata
______________________

This action updates the draft deposit with new information.

- HTTP method: ``PATCH``

- URL path: ``/api/objects/NAMESPACE/OBJECT_ID``

- Required parameters: token

- Payload data: the metadata for the draft deposit to be updated, in the JSON Patch format (see http://jsonpatch.com/)

- Status code on success: ``200``

- Returns: the updated metadata of the draft deposit.

- Notes: The JSON Patch format contains one or more JSONPath strings. The root of these paths are the metadata object, as this is the only mutable object. For instance, to update the title field of the deposit, use this JSONPath: /titles/title

Example 1
-----------

The following example adds two values to the metadata field `keywords` of an existing draft deposit.

Command:

``curl -X PATCH -H 'Content-Type:application/json-patch+json' -d '[{"op": "add", "path":"/keywords", "value": ["keyword1", "keyword2"]}]' "https://$SDR_HOST/api/objects/$NAMESPACE/$OBJECT_ID?token=$TOKEN"``

Returns:

.. code-block:: json

  {
    "created": "2016-10-24T12:21:21.697737+00:00",
    "id": "01826ff3e4974415afdb2574a7ea5a91",
    "links": {
      "files": "https://trng-repository.surfsara.nl/api/files/5594a1bf-1484-4a01-b7d3-f1eb3d2e1dc6",
      "publication": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91",
      "self": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91/draft",
      "versions": "https://trng-repository.surfsara.nl/api/objects/d855e187e3864ddcaa1b68625866dd78/versions"
    },
    "metadata": {
      "$schema": "https://trng-repository.surfsara.nl/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095/schemas/0#/draft_json_schema",
      "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
      "community_specific": {},
      "keywords": [
        "keyword1",
        "keyword2"
      ],
      "open_access": true,
      "owners": [
        8
      ],
      "publication_state": "draft",
      "titles": [
        {
          "title": "My community title"
        }
      ]
    },
    "updated": "2016-10-24T12:23:59.454951+00:00"
  }

Example 2
-----------

This example replaces the value of the title of a deposit. This requires a JSONPath ``/title`` as we are updated an existing value of multivalued field.

Command:

``curl -X PATCH -H 'Content-Type:application/json-patch+json' -d '[{"op": "replace", "path":"/title", "value": ["The new title"]}]' "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID?token=$TOKEN"``

Returns:

.. code-block:: json

  {
    "created": "2016-10-24T12:21:21.697737+00:00",
    "id": "01826ff3e4974415afdb2574a7ea5a91",
    "links": {
      "files": "https://trng-repository.surfsara.nl/api/files/5594a1bf-1484-4a01-b7d3-f1eb3d2e1dc6",
      "publication": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91",
      "self": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91/draft",
      "versions": "https://trng-repository.surfsara.nl/api/objects/d855e187e3864ddcaa1b68625866dd78/versions"
    },
    "metadata": {
      "$schema": "https://trng-repository.surfsara.nl/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095/schemas/0#/draft_json_schema",
      "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
      "community_specific": {},
      "open_access": true,
      "owners": [
        8
      ],
      "publication_state": "draft",
      "titles": [
        {
          "title": "The new title"
        }
      ]
    },
    "updated": "2016-10-24T12:23:59.454951+00:00"
  }

Example 3
-----------

The next example updates the community-specific metadata fields ``field_1`` and ``field_2`` of an existing draft deposit of community with identifier ``community:surf``. Note that in order to update a community-specific field, the JSONPath `/community/FIELD_NAME` is required.

Command:

``curl -X POST -H "Content-Type:application/json-patch+json" -d '[{"op": "add", "path": "/community/field_1", "value": "value_1"}, {"op": "add", "path": "/community/field_2", "value": "value_2"}]' "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID?token=$TOKEN"``

Returns:

.. code-block:: json

  {
    "created": "2016-10-24T12:21:21.697737+00:00",
    "id": "01826ff3e4974415afdb2574a7ea5a91",
    "links": {
      "files": "https://trng-repository.surfsara.nl/api/files/5594a1bf-1484-4a01-b7d3-f1eb3d2e1dc6",
      "publication": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91",
      "self": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91/draft",
      "versions": "https://trng-repository.surfsara.nl/api/objects/d855e187e3864ddcaa1b68625866dd78/versions"
    },
    "metadata": {
      "$schema": "https://trng-repository.surfsara.nl/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095/schemas/0#/draft_json_schema",
      "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
      "community_specific": {
        "field_1": "value_1",
        "field_2": "value_2"
      },
      "open_access": true,
      "owners": [
        8
      ],
      "publication_state": "draft",
      "titles": [
        {
          "title": "My dataset deposit"
        }
      ]
    },
    "updated": "2016-10-24T12:21:21.697744+00:00"
  }

Common errors
-------------

On JSON Patch operation error:

.. code-block:: json

  {
    "message": "Invalid Operation.",
    "errors": [
      {
        "message": "Invalid JSON Pointer"
      }
    ],
    "status": 400
  }

One of the JSON Patch operations is invalid.

On JSON Patch content type error:

.. code-block:: json

  {
    "message": "Invalid 'Content-Type' header. Expected one of: application/json-patch+json",
    "status": 415
  }

The supplied content type header value is invalid.

On metadata validation error:

.. code-block:: json

  {
    "message": "Validation error.",
    "errors": [
      {
        "message": "{'title': 'Some title'} is not of type 'array'",
        "field": "titles"
      }
    ],
    "status": 400
  }

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

- Notes: you must provide the external references using EPIC PIDs and therefore you need to be able to register new PIDs with an EPIC PID hosting institute using a registered prefix. It is possible to get a prefix through EUDAT, please use the contact form for this.

Command:

``curl -X PATCH -H 'Accept:application/json-patch+json' -d '' "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID?token=$TOKEN"``

.. _rest-api-ref-submit-draft-deposit-for-publication:

Submit draft deposit for publication
______________________

This action marks the draft deposit as complete and submits it for publication. Currently Data Repository automatically publishes all the submitted drafts. Please be advised that publishing the draft will make its files immutable.

A draft deposit is submitted for publication if a special metadata field, called 'publication_state' is set to 'submitted'. This field can be set using the metadata update request described above.

Depending on the community specification, other fields could be required in order to successfully publish a deposit. In case one of the required fields is missing the request fails and an error message is returned with further details.

- HTTP method: ``POST``

- URL path: ``/api/objects/$NAMESPACE/$DEPOSIT_ID/submit``

- Required parameters: ``token``

- Payload data: None

- Status code on success: ``200``

- Notes: this request is essentially a metadata update request as described above.

Command:

``curl -X POST "https://$SDR_HOST/api/objects/$NAMESPACE/$DEPOSIT_ID/submit?token=$TOKEN"``

Returns:

.. code-block:: json

  {
    "created": "2016-10-24T12:21:21.697737+00:00",
    "id": "01826ff3e4974415afdb2574a7ea5a91",
    "links": {
      "files": "https://trng-repository.surfsara.nl/api/files/5594a1bf-1484-4a01-b7d3-f1eb3d2e1dc6",
      "publication": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91",
      "versions": "https://trng-repository.surfsara.nl/api/objects/c1d28e53db104cb286425902af134579/versions",
      "self": "https://trng-repository.surfsara.nl/api/objects/01826ff3e4974415afdb2574a7ea5a91/draft"
    },
    "metadata": {
      "$schema": "https://trng-repository.surfsara.nl/api/communities/e9b9792e-79fb-4b07-b6b4-b9c2bd06d095/schemas/0#/draft_json_schema",
      "DOI": "10.5072/b2share.cdb15c27-326e-4e95-b812-6b1c6b54c299",
      "community": "e9b9792e-79fb-4b07-b6b4-b9c2bd06d095",
      "community_specific": {},
      "keywords": [
        "keyword1",
        "keyword2"
      ],
      "ePIC_PID": "http://hdl.handle.net/11304/2c473f04-d997-47d9-9bdb-d3d71800f870",
      "open_access": true,
      "owners": [
        8
      ],
      "publication_state": "published",
      "titles": [
        {
          "title": "TestRest"
        }
      ]
    },
    "updated": "2016-10-24T12:26:51.538025+00:00"
  }

.. _rest-api-ref-update-published-deposit-metadata:

Update published deposit metadata
______________________

This request updates the metadata of an already published deposit without creating a new version.

- HTTP method: ``PATCH``

- URL path: ``/api/objects/NAMESPACE/DEPOSIT_ID/``

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

Delete a published object.

- HTTP method: ``DELETE``

- URL path: ``/api/objects/NAMESPACE/DEPOSIT_ID``

- Required parameters: token

- Status code on success: ``204``

- Returns: no contents.

- Notes: only a site administrator can delete a published object.

Command:

``curl -X DELETE "https://$SDR_HOST/api/objects/NAMESPACE/$DEPOSIT_ID/?token=$TOKEN"``
