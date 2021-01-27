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

This page will explain the basic concepts, authentication and all existing HTTP requests that can currently be used. The given examples are explained using curl commands.

.. _using-the-api:

==================
Using the API
==================

The REST API is used by making API requests using the `methods`_ of the standard HTTP protocol. Typically an application like curl is used to make requests, but it is also possible to do this from within your custom-built applications.

If a request is received by the Data Repository, it will be processed and a response will be given. This response is according to the HTTP protocol and will include a `status codes`_ indicating whether the processing was successful or an error occured. Based on this code a body is included that either gives the updated state of the object being requested or modified, or a description of the error that occurred.

By making a set of requests successively, an existing object can be modified in its description, relationship to other objects or visibility on the web interface. More importantly, new objects can be created from scratch that contain descriptive metadata and files for publication.

.. _rest-api-integration-python:

Integration with Python
_________________

To intergrate the API in your application using Python, please make use of the 'requests' package that allows excellent and straightforward interaction possibilities from within your Python scripts.

.. _rest-api-authentication:

==================
Authentication
==================

Although listing and accessing public data is not access-controlled, only registered users can use the API to its full extent. Authentication during requests is done by passing an access token along with the request. The access token is an randomly-generated string which can be created in the Data Repository user account page after logging in to the web user interface. See :ref:`API tokens <account-api-tokens>`.

.. _using-the-api:

==================
Using the REST API
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
GET          Typically no              Get current state of an object or resource,
									   including header information
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

.. Links:

.. _`methods`: https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods
.. _`status codes`: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes