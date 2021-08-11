.. _deposit:

*************
Deposit data
*************

The process of getting data into the data repository and publishing it is called depositing. This can be done using the online deposit workflow that is part of the Data Repository service. Only registered users can deposit data and create publications. Once the deposit is complete, you will have a publication for your dataset.

.. warning:: Use the `training instance`_ to create test uploads, the `production instance`_ is for publications only.

.. contents::
    :depth: 8

.. _prepare-data:

Prepare data
============

To prepare data for a deposit there are some best practices for the file format, file size, metadata, data documentation and structuring. For more information, visit the :ref:`best practices <best-practices>` page.

.. _deposit-workflow:

Deposit via the browser
=======================

To deposit a new data set login to the service and use the ``Deposit now`` or ``Upload`` button to start the process. This process consists of the following three steps:

1. On the 'Create a new deposit' page, use the ``Add files`` button to select the files to deposit and click ``Start upload`` to upload the file(s).

   .. note:: Make sure that all files are uploaded in an acceptable file format. Valid file formats can be found on the `file formats`_ documentation page. If the data format you are trying to upload is not supported, please contact the helpdesk.

   Provide the basic metadata for your deposit such as the title, creator(s), keywords (for searching purposes) and description. The fields marked with a * are mandatory metadata fields.

   .. image:: ../img/deposit-workflow-1.png
    :align: center
    :width: 90%

   To set the appropriate license for the publication use the ``Select`` button to choose one of the available licenses. If you are not sure which license to choose, answer the questions on the top of the built-in wizard form to find the appropriate license.

   .. image:: ../img/license.png
    :align: center
    :width: 75%

   Once all meta-data is complete, click ``Next >>`` to go to the second step of the online deposit workflow.

2. To make the deposit discoverable you must select a community, and optionally a collection and/or a metadata schema (if possible). If you are a member of a community and you want to deposit data in that community, select the community name. The available collections will be pre-populated based on which community you choose and which collections you have created yourself.

   If a community or collection is associated with a metadata schema, you will be presented with a community or collection metadata form. The fields marked with a * are mandatory metadata fields.

   .. image:: ../img/deposit-workflow-2.png
    :align: center
    :width: 90%

   Once all metadata is complete, click ``Next >>`` to go to the third and final step of the online deposit workflow.

3. In the final step you can fill in optional information such as the embargo data of your data (if configured). You can also specify links that are related to this publication. If you have any additional metadata that does not fit the basic or community metadata fields, you can add them here. For every field there needs to be a unique field name and a value. Finally, carefully read the `Terms of use`_ and `Data Producer Agreement`_ before checking the checkbox.

   .. image:: ../img/deposit-workflow-3.png
    :align: center
    :width: 90%

   When you have checked all metadata in the right sidebar, click on the ``Complete`` button to finalize your deposit.

.. _deposit-rest-api-:

Deposit via the REST API
========================

If you have many deposits to create, or have an automated workflow set up or application that generates data that needs to be published, you can make use of the REST API provided by the service. Please refer to the :ref:`REST API <rest-api>` page for more information.

.. Links:

.. _`training instance`: https://trng-repository.surfsara.nl
.. _`production instance`: https://repository.surfsara.nl
.. _`file formats`: https://repository.surfsara.nl/docs/formats
.. _`Terms of Use`: https://repository.surfsara.nl/docs/terms
.. _`Data Producer Agreement`: https://repository.surfsara.nl/docs/data-producer
