.. _rest-api:

**************
REST API
**************

This page provides information about the REST API of the Data Repository service.

.. contents::
    :depth: 4

.. _rest-api-introduction:

==================
Introduction
==================

The Data Repository service provides a graphical, web-based interface, whose functionality is discussed in the corresponding user documentation pages.

The Data Repository REST API can be used for interaction with the service via external services or applications, for example for integration with other websites (research community portals) or for uploading or downloading large data sets that are not easily handled via a web browser.

This page will explain the basic concepts, authentication and all existing HTTP requests that can currently be used. In the next pages, the examples given are done using cURL commands. This tool can be freely downloaded for any OS.

.. _rest-api-basic-concepts:

==================
Basic concepts
==================

The Data Repository service uses several concepts which are briefly explained below.

A scientific community has the roles of creating and maintaining metadata schemas and curating the datasets which are part of a scientific domain or research project. Users of the Data Repository can be part of one or more communities. Some selected members of a community are also given the role of community administrators, which grants them the special rights needed for the schema definitions and deposit curation tasks.

Any registered user can upload scientific datasets into Data Repository and thus create data deposits. A deposit is comprised of data files and associated metadata. The deposit’s metadata consists of a set of common fixed metadata fields and a set of custom metadata blocks, each block containing related metadata fields. A deposit is always connected to one scientific community which has the role of curating and maintaining it (except for deposits created as part of the generic SURF community).

A deposit contains a set of common metadata fields and a set of custom metadata blocks. This metadata is not free form, however, but is governed by static schemas; the common metadata schema is set by Data Repository and defines a superset of Dublin Core elements, while the schema for the custom metadata block is specific to each community and can be customized by the community administrators. In order to be accepted, the deposits submitted to a community must conform to the schema required by the community.

.. _rest-api-objects:

==================
Modifying objects
==================

A deposit or collection can exist in several states. Immediately after creation a deposit enters the 'draft' state. In this state the deposit is only accessible by its owner and can be freely modified: its metadata can be changed and files can be uploaded into or removed from it. A draft can be published at any time, and through this action it changes its state from 'draft' to 'published', is assigned persistent identifiers, and becomes publicly accessible. Please note that after publication, the list of files in a published deposit cannot be changed.

To update the metadata of a deposit through the API, a `JSON Patch`_ must be supplied with the request. Please read the documentation on this website carefully to fully understand how these patches work. In the request below, the term 'JSONPath' is used which indicates a path in the metadata relative to the root of the structure.

.. _rest-api-making-requests:

==================
Making requests
==================

The REST API is used by making API requests using the `methods`_ of the standard HTTP protocol. Typically an application like curl is used to make requests, but it is also possible to do this from within your custom-built applications.

If a request is received by the Data Repository, it will be processed and a response will be given. This response is according to the HTTP protocol and will include a `status codes`_ indicating whether the processing was successful or an error occured. Based on this code a body is included that either gives the updated state of the object being requested or modified, or a description of the error that occurred.

All requests that provide data must be formatted in JSON or JSON Patch, indicated by the ``Content-type`` header valued ``application/json;charset=UTF-8`` or ``application/json-patch+json;charset=UTF-8`` respectively. This generally only applies to requests that use the POST or PATCH method.

By making a set of requests successively, an existing object can be modified in its description, relationship to other objects or visibility on the web interface. More importantly, new objects can be created from scratch that contain descriptive metadata and files for publication.

.. _rest-api-making-responses:

Responses
_________________

All request responses will be in JSON format and UTF-8 encoded, indicated by the ``Content-type`` header valued ``application/json;charset=UTF-8``.

A deposit is represented as a JSON object:

.. code-block:: json

	{
	  "field1": "value"
	}


A collection of deposits is represented as a JSON array of objects:

.. code-block:: json

	{
	  "collection": [
	    {
	      "field1": "value",
	      "field2": "value"
	    },
	    {
	      "field1": "value",
	      "field2": "value"
	    }
	  ]
	}


Timestamps are in UTC and formatted according to ISO 8601:

.. code-block:: json

	{
	  "updated": "YYYY-MM-DDTHH:MM:SS.ssssss+00:00"
	}

In case a request fails, the body of the response body contains details about the error, for Command:

.. code-block:: json

	{
	  "message": "The requested URL was not found on the server.  If you entered the URL manually please check your spelling and try again.",
	  "code": 404
	}

Herein the message field provides a detailed description of what went wrong, while the code indicates the HTTP status code (equivalent to the request response status code).

.. _rest-api-status-codes:

Status codes
_________________

The request status codes indicate whether the request was successfully received, processed and/or executed. The Data Repository service follows the globally accepted list of HTTP status codes in all cases.

One of the following status codes is returned in case the request was successful:

    ``200`` - Request was successfully received and executed, see body for results

    ``201`` - Object created, see body for results

    ``204`` - No contents, this occurs when for example an object is successfully deleted

In case the request failed, the body of the response usually contains details, and one of the following status codes is returned:

    ``400`` - Request was not understood

    ``401`` - User must authenticate first, usually because no access token was provided with the request

    ``403`` - User is not authorized to perform request, missing permission to do so

    ``404`` - Requested object not found or API endpoint does not exist

Any status code greater then or equal to 500 indicates that internally something went wrong in the server. If in this case the problem persists, kindly report this to SURF.

.. _rest-api-authentication:

==================
Authentication
==================

Although listing and accessing public data is not access-controlled, only registered users can use the API to its full extent. Authentication during requests is done by passing an access token along with the request. The access token is an randomly-generated string which can be created in the Data Repository user account page after logging in to the web user interface. See :ref:`API tokens <account-api-tokens>`.

.. _rest-api-general-usage:

==================
General usage
==================

The general command to use the REST API looks as follows (using cURL):

``curl https://$SDR_HOST/api/$PATH``

where ``SDR_HOST`` is the Data Repository host you want to communicate with (typically repository.surfsara.nl) and ``PATH`` is the endpoint to use. An endpoint uniquely identifies the resource(s) you are requesting or want to modify. See below for more information.

To authenticate yourself during a request, use the ``token`` parameter (see :ref:`API tokens <account-api-tokens>` to generate a token):

``curl https://$SDR_HOST/api/$PATH?token=$TOKEN``

Depending on the result you want to achieve and the request you want to make, you can change the method for the request (default GET), e.g. to post a change to specific deposit (see also next section):

``curl -X POST https://$SDR_HOST/api/objects/deposit/1?token=$TOKEN``

.. _rest-api-methods:

Methods
_________________

In the table below, the most used HTTP methods for interaction using the REST API are listed.

============ =======================   =============
Method       Authentication required   Typical use
============ =======================   =============
GET          Typically no              Get current state of an object or resource, including header information
POST         Yes                       Create new object
PUT          Yes                       Upload file to deposit
PATCH        Yes                       Update descriptive metadata state of an object or resource
DELETE       Yes                       Delete a (part of a) resource or object
HEAD         Typically no              Identical to GET method, but without response body
============ =======================   =============

.. _rest-api-endpoints:

Endpoints
_________________

An endpoint uniquely identifies the resource(s) you are requesting or want to modify. An endpoint always starts with the general ``/api`` part and is logically followed by the type of information represented in the endpoint. Optionally a unique identifier that represents a resource or object can be added.

In the table below, some endpoints are listed together with the available methods:

======================================= ====================== =============
Endpoint                                Methods                Description
======================================= ====================== =============
``/api``                                GET                    General information about the REST API
``/api/objects``                        GET                    Object listing and search (with parameters)
``/api/objects/deposit/<id>``           GET, POST, PATCH       Deposit metadata retrieval or updates
``/api/objects/collection/<id>``        GET, POST, PATCH       Collection metadata retrieval or updates
``/api/objects/community/<id>``         GET                    Community metadata retrieval
``/api/objects/group/<id>``             GET                    Group metadata retrieval
``/api/objects/schema/<id>``            GET                    Schema metadata retrieval
======================================= ====================== =============

.. _rest-api-objects:

Objects
_________________

In the table below, the available object types and corresponding operations for interaction using the REST API are listed.

============ ==============
Type         Operations
============ ==============
Deposit      List, retrieve, create, modify, publish, delete (draft)
Collection   List, retrieve, modify, publish, delete (draft)
Community    List, retrieve
Group        List, retrieve
Schema       List, retrieve
============ ==============

.. _rest-api-integration:

==================
Integration
==================

The Data Repository REST API can be integrated in any workflow or application as long as they adhere to the required workflows.

.. _rest-api-integration-python:

Integration with Python
_________________

To intergrate the API in your application using Python, please make use of the 'requests' package that allows excellent and straightforward interaction possibilities from within your Python scripts.


.. Links:

.. _`methods`: https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods
.. _`status codes`: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
.. _`JSON Patch`: http://jsonpatch.com/