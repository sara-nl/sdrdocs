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

If a request is received by the Data Repository, it will be processed and a response will be given. This response is according to the HTTP protocol and will include a `status code`_ indicating whether the processing was successful or an error occured. Based on this code a body is included that either gives the updated state of the object being requested or modified, or a description of the error that occurred.

By making a set of requests successively, an existing object can be modified in its description, relationship to other objects or visibility on the web interface. More importantly, new objects can be created from scratch that contain descriptive metadata and files for publication.

.. _rest-api-integration:

Integration
_________________

To intergrate the API in your application using Python, please make use of the 'requests' package that allows excellent and straightforward interaction possibilities from within your Python scripts.

.. _rest-api-authentication:

==================
Authentication
==================

Although listing and accessing public data is not access-controlled, only registered users can use the API to its full extent. Authentication during requests is done by passing an access token along with the request. The access token is an randomly-generated string which can be created in the Data Repository user account page after logging in to the web user interface. See

.. _using-the-api:

==================
Using the REST API
==================

The general command to use the REST API looks as follows (using cURL):

``curl https://$SDR_HOST/api/$PATH``

To authenticate yourself during a request, use the ``token`` parameter (see :ref:`API tokens <api-token>` to generate a token):

``curl https://$SDR_HOST/api/$PATH?token=$TOKEN``

.. Links:

.. _`methods`: https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods
.. _`status codes`: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes