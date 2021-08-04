.. _advanced-objects:

*****************
Objects
*****************

This page provides general information about objects stored in the Data Repository.

.. contents::
    :depth: 2

.. _advanced-objects-general:

==============================
Objects
==============================

Digital objects are stored and maintained by the repository service using a dedicated object storage and definition system. The objects contain metadata defined in XML and in case of deposits also the references to files.

==============================
Object types
==============================

In the Data Repository service several types of objects exist with each having its own function.

.. _advanced-objects-deposit:

Deposits
_________________

A deposit is an object containing one or more files and is described by a set of metadata and can be referred to by a unique DOI and/or PID.

Deposits have their own landing page that give a complete description of the object. Deposits are indexed for search and can be harvested by external metadata catalogues.

.. _advanced-objects-collection:

Collections
_________________

A collection is an object containing one or more deposits or other collections and is described by a set of metadata and can be referred to by a unique DOI and/or PID. Collections do not contain files.

Collections have their own landing page that give a complete description of the object. They are indexed for search and can be harvested by external metadata catalogues.

.. _advanced-objects-communities:

Communities
_________________

A community is an object that can contain one or more deposits or other collections. It is described by a minimum set of metadata and can be referred to by a unique PID. Communities do not contain files.

Communities have their own landing page that give an overview of the objects contained. They are indexed for search.

.. _advanced-objects-schemas:

Schemas
_________________

A schema is an object that can defines a set of metadata fields. Schemas are used to enable validation and enforcement of metadata for other objects, such as deposits and collections.

Schemas have their own landing page that give an overview of the metadata fields. They are indexed for search.


.. _advanced-objects-access:

==============================
Object-level access
==============================

By default, an object is publicly accessible and therefore can be seen and downloaded by anyone interested. This includes all files and the metadata, except access statistics and configuration. To restrict access to an object, the owner or an administrator of the object can set the access levels. In the table below these restrictions are listed.

============  =========== ========
Access level  Per user    Description
============  =========== ========
Open public   No          Object, including files and metadata, is open access and accessible to everyone, even anonymous users
Registered    No          Object is accessible only to registered users. Anonymous users can still see metadata, but cannot download files.
Closed        Yes         Object is only accessible to users specifically given access to it. Metadata is still open.
============  =========== ========

If an object is set to closed access, the owner or an administrator can select users that are allowed to access the object. All other users will receive an 'object not found' message.

