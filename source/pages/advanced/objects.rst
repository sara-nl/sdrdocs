.. _get-access:

*****************
Objects
*****************

This page provides general information about objects stored in the Data Repository.

.. contents::
    :depth: 2

.. _objects-general:

==============================
Objects
==============================

Digital objects are stored and maintained by the repository service using a dedicated object storage and definition system. The objects contain metadata defined in XML and in case of deposits also the references to files.

.. _objects-general:

==============================
Object-level access
==============================

By default, an object is publicly accessible and therefore can be seen and downloaded by anyone interested. This includes all files and the metadata, except access statistics and configuration. To restrict access to an object, the owner or an administrator of the object can set the access levels. In the table below these restrictions are listed.

============ =========== ========
Access level Per user    Description
============ =========== ========
Public       No          Object, including files and metadata, is open access and accessible to everyone, even anonymous users
Registered   No          Object is accessible only to registered users. Anonymous users can still see metadata, but cannot download files
Private      Yes         Object is only accessible to users specifically given access to it. Metadata is still open though.
============ =========== ========

If an object is set to private access, the owner or an administrator can select users that are allowed to access the object. All other users will receive an 'object not found' message.
