.. _metadata:

***********
Metadata
***********

In the Data Repository service, any digital resource is identified and described by metadata. In order to increase the findability, visibility and understanding of your publication or any related object, metadata is added that describes the object using a pre-defined set of fields.

.. contents::
    :depth: 8

.. _metadata-default:

==============
Default metadata
==============

Every digital resource must be described by a number of default set of metadata fields in order to uniquely identify it. Some of these fields are optional, but it is recommended to provide as much information as possible.

Without the mandatory fields provided, the repository will not allow completing the publication.

The set of metadata fields is based on the `Dublin Core metadata definition v1.1`_. The following fields are mandatory:

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

==============
Community metadata
==============

If an object is published under a community, it is possible that additional fields need to be provided before a publication can be completed. If some of these fields are mandatory, a publication cannot be completed without providing the values for these fields.

.. _metadata-collection:

==============
Collection metadata
==============

In addition to the community metadata fields, an object can be published under a collection. Again, it is possible that additional fields need to be provided before a publication can be completed. If some of these fields are mandatory, a publication cannot be completed without providing the values for these fields.

.. Links:

.. _`Dublin Core metadata definition v1.1`: https://www.dublincore.org/specifications/dublin-core/dcmi-terms/
