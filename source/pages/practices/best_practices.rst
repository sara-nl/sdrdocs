.. _best-practices:

**************
Best Practices
**************

This page provides information on best practices while using the repository.

.. contents::
    :depth: 4

.. _prepare-data:

==================
Preparing data
==================

To prepare data for a deposit you need to consider the following points:

.. _file-formats:

File formats
_________________

By default, the repository does not accept all file formats. This is to ensure future compatibility, understanding and support of published data by the repository itself, but also by other users. The repository distinguishes two kinds of formats: preferred and accepted formats.

- **Preferred formats** are file formats of which SURF is confident that they will offer the best long-term guarantees in terms of usability, accessibility and sustainability. Depositing research data in preferred formats will always be accepted by SURF. Here is a list with `SURF preferred formats`_ .

- **Acceptable formats** are file formats that are widely used in addition to the preferred formats, and which will be moderately to reasonably usable, accessible and robust in the long term. SURF favours the use of preferred formats, but acceptable formats will in most cases also be allowed. Here is a list with `SURF acceptable formats`_ .

If you think your file format should be accepted by the repository, but is currently not on one of the lists, please contact us. A reason could be that a community uses a file format that is widely used within that community but not outside of it.

.. _file-size:

File sizes and count
____________________

- **Maximum file size**: 4 GB using the online deposit form

The maximum deposit data volume is 10 GB and the maximum number of files that can be uploaded via the onlone deposite is 10 files. If you want to deposit larger volumes of data or larger number of files in a single deposit, please contact us.

.. _data-documentation:

Data documentation
__________________

Data documentation ensures that research data are understood and therefore used by current and future users (including the researcher). It is vital to store the data in a structured and consistent way with appropriate data documentation. The documentation can be a description explaining what the data is, what you can do with it and how it can be used. Even more technical documentation about the exact file format could be of use. Documentation can be provided in one of the accepted or preferred file formats.

.. _best-practices-metadata:

Metadata
_________________

Metadata provides structured information about the data. Depending on the type of data, there are different types of metadata:

- **Descriptive metadata** describes and identifies information resources (minimal metdata required to find a digital object). In includes elements such as title, abstract, author, and keywords

- **Structural metadata** provides information about the internal structure of resources including page, section, chapter numbering, indexes, and relations to other digital objects.

- **Technical metadata** provides information on the technical aspects of the datasets such as data formats, hardware/software used, calibration, version, authentication, encryption.

- **Administrative metadata** provides information on user rights and management of digital objects such as license, rights management, and access control.

The repository will only ask for descriptive metadata during the deposit workflow, but it is highly recommended to add links to additional documentation or files containing metadata of any kind. Any other kinds of metadata are automatically added, though not always visible for the end-user.

.. _data-organisation:

Data organisation
_________________

If you want your research data to be easily found and interpreted, the collection and deposit structure and the file names used for the data files should be logical and straightforward. Make sure to use the correct file extensions to avoid files being rejected or misinterpreted by other users. Its also a good practice to note the file naming and its meaning in a separate readme file.

You can create collections and collections of other collections to structure your data. There is no limit on the number of deposits in a single collection.

.. _data-anonymization:

Data anonymization
__________________

Before you upload the files you should check whether they contain privacy-sensitive information within the meaning of the regulations and guidelines in the `General Data Protection Regulation`_ (GDPR). If you give access to the data publicly or any other user, the data must be completely anonimyzed.

.. Links:

.. _`SURF preferred formats`: https://repository.surfsara.nl/docs/formats
.. _`SURF acceptable formats`: https://repository.surfsara.nl/docs/formats
.. _`General Data Protection Regulation`: https://www.government.nl/privacy
