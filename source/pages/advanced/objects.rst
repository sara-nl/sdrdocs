.. _advanced-objects:

*****************
Objects reference
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

.. _advanced-objects-deposits:

Deposits
_________________

A deposit is an object containing one or more files and is described by a set of metadata and can be referred to by a unique DOI and/or PID.

Deposits have their own landing page that give a complete description of the object. Deposits are indexed for search and can be harvested by external metadata catalogues.

.. _advanced-objects-collections:

Collections
_________________

A collection is a bundle of a (large) number of deposits and/or collections. Collections allow to create structure in your publications and make your data easier to understand and find. Collection are annotated using similar metadata as deposits and can be referred to by a unique DOI and/or PID. Collections do not contain files.

Collections have their own landing page that give a complete description of the object. They are indexed for search and can be harvested by external metadata catalogues.

.. _advanced-objects-communities:

Communities
_________________

A community bundles collections and deposits under a single entity. With a community, you can add policies to deposit workflows that make sure publications are up to the standards of your community. It is described by a minimum set of metadata and can be referred to by a unique PID. Communities do not contain files.

Communities can have user members with specific roles, such as the community administrator or simply a member. Depending on the policies set, a user has specific priviledges concerning the community.

Communities have their own landing page that give an overview of the objects contained. They are indexed for search.

.. _advanced-objects-schemas:

Metadata schemas
_________________

A metadata schema is an object that defines a set of metadata fields and is essentially a logical plan showing the relationships between metadata fields, normally through establishing rules for the use and management of metadata. Metadata schema makes sure that your deposit or collection has complete and understandable information attached to it.

Schemas have their own landing page that give an overview of the metadata fields. They are indexed for search.

.. _advanced-objects-groups:

Groups
_________________

A group is a bundling of one or more users. They can be used to provide access or administrative privileges to specific objects for a selection of persons using only a single relation.

Groups have their own landing page that give an overview of the managed objects. They are indexed for search.


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

