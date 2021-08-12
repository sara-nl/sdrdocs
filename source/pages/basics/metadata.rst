********
Metadata
********

In the Data Repository service, any deposit is identified and described by metadata. In order to increase the findability, visibility and understanding of your deposit and any related object, metadata is added to describe the deposit using a pre-defined set of fields.

.. contents::
    :depth: 8

.. _metadata-default:

Default metadata
================

Every deposit or collection must be described by a default set of metadata fields in order to uniquely identify it. Some of these fields are optional, but it is recommended to provide as much information as possible. The set of metadata fields is based on the `Dublin Core metadata definition v1.1`_. The following fields are mandatory:

================= =========== =============
Field name        Type        Description
================= =========== =============
Title             String      Title of publication
Creator           String      Name(s) of principle creator. Use full names as much as possible
Description       Text        Description (or abstract) of the article or dataset
Keywords          String      Keyword(s) or subject(s) of deposit
Publication date  Date        Original date of publication
License           String      Open access license to display when viewing or downloading the dataset
================= =========== =============

The following fields are optional:

================= =========== =============
Field name        Type        Description
================= =========== =============
Type              String      Type of data
File format       String      Primary file format or mime-type of the files in the dataset
Publisher         String      Publisher of the article or dataset
Contributor       String      Additional contributors to the publication
Language          String      Primary language used in the dataset
Discipline        String      Select the discipline that matches closest to the data contained in the publication
Contact email     String      Contact email address for users
================= =========== =============

.. _metadata-community:

Community metadata
==================

Some communities may provide an additional set of metadata fields. Some of these fields might be mandatory and need to be filled in before the object can be published in the community.

.. _metadata-collection:

Collection metadata
===================

In addition to a community, an object can also be published under a collection. Some collections may provide additional optional or required metadata fields that need to be provided before a publication can be completed.

.. Links:

.. _`Dublin Core metadata definition v1.1`: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/
