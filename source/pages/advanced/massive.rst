.. _massive:

**********************
Large-scale depositing
**********************

This page explains how to get your large-scale dataset into the data repository. It requires access to the storage infrastructure of SURF and assistance of an advisor.

Depositing is the act of uploading data to the Data Repository. Only registered users are permitted to deposit data and create publications.

When your dataset is very large in size and/or number of files, it is much more efficient to upload your data to the storage infrastructure of SURF and publish data from there. Generally, any dataset larger than 100 GB can be considered large-scale and this workflow applies.

You don't have access by default to the storage infrastructure, so please contact an advisor in order to assist you on this.

Uploading data via the REST API
_______________________________

The Data Repository service provides a REST API that enables users to upload data and create deposits and other objects via tools or the command line. See the :ref:`REST API <rest-api>` page of this help documentation.

.. contents::
    :depth: 8

.. _creating-deposits:

============================
Creating deposits
============================

Contrary to the online deposit workflow some steps in the creation of deposits change in the large-scale deposit workflow.

.. _prepare-data-massive:

Prepare data
______________

To prepare data for a large-scale deposit, there are some best practices for e.g. the file format, file size, metadata, data documentation and structuring. For more information, visit the :ref:`Best Practices <best-practices>` page.

.. _ingesting-data:

Ingestion
______________

Once you have access to the storage infrastructure, you can start uploading data using your favourite file transfer tool.

You can create folders and rename files so the structure of the publication is immediately clear.

.. _annonating-deposit:

Annotation
______________

You can send your metadata to the advisor that is helping you publishing your dataset. The metadata will be attached to the files as soon as the publication is finalized.

.. _publishing-deposit:

Publication
______________

Once the structure and annotation of all deposits are complete, the advisor will initiate a procedure that publishing all objects. This is done using internally developed tooling. Your data will be moved to a secure location and is no longer accessible from anywhere other than the Data Repository service.
