.. _rest-api-workflow-deposits:

**************
REST API workflow for deposits
**************

This page provides information about creating and managging deposit using the REST API of the Data Repository service.

.. contents::
    :depth: 4

.. _rest-api-general-workflow:

==================
General publication workflow
==================

The HTTP REST API does not impose a specific workflow for creating a deposit. The following example workflow only defines the most basic steps:

- Identify a target community for your data by using the REST API :ref:`List all communities <rest-api-list-all-communities>` request
- Using the community's identifier, retrieve the JSON Schema of the deposit's metadata. The submitted metadata will have to conform to this schema. Use the :ref:`Get community schema <rest-api-get-community-schema>` request.
- Create a draft deposit: use the :ref:'Create draft deposit <rest-api-create-draft-deposit>` request.
- Upload the files into the draft deposit. You will have to use one HTTP request per file. Use the :ref:`Upload file <rest-api-upload-file>` request.
- Set the complete metadata and publish the deposit. Use the :ref:`Submit draft for publication <rest-api-submit-draft-for-publication>` request.
