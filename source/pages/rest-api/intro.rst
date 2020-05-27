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

The REST API is used by making API requests using the GET or POST methods of the standard HTTP protocol. Typically an application like curl is used to make requests, but it is also possible to do this from within your custom-built applications. To intergrate the API in your application using Python, please make use of the 'requests' package that allows excellent and straightforward interaction possibilities from within your Python scripts.

.. _rest-api-authentication

==================
Authentication
==================

Although listing and accessing public data is not access-controlled, only authenticated users can use the API to its full extent. Authentication during requests is done by passing an API token along with the request. The API token is an encrypted string which can be created in the Data Repository user account page after logging in to the web user interface.
