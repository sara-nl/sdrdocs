.. _deposit:

***********
Deposit
***********

The process of getting data into the data repository and publishing it is called depositing. This can be done using the online deposit workflow that is part of the Data Repository service. Once depositing is completed, you will have a publication for your dataset.

.. contents::
    :depth: 8


.. _deposit-data:

==============
Deposit data
==============

Only registered users can deposit data and create publications.

.. _prepare-data:

Prepare data
______________

To prepare data for a deposit there are some best practices for the file format, file size, metadata, data documentation and structuring. For more information, visit the :ref:`Best Practices <best-practices>` page.

.. _deposit-workflow:

Deposit workflow
_________________

Clicking the deposit link in the main page opens the first of the three steps required to create a publication. The steps are as follows:

1. In the 'Create a new deposit' page, select files to deposit and then click on 'Start upload' to upload the file(s).

 .. note:: Make sure that you are uploading an acceptable file format. Valid file formats can be found on the `File formats`_ documentation page. If the data format you are trying to upload is not supported, you can always contact us for support.

 Provide the basic metadata for your deposit such as the title, creator(s), keywords (for searching purposes) and description. The fields in the upper section are mandatory fields, while the optional fields are shown in the lower section.

 .. image:: ../img/deposit-workflow-1.png
   :align: center
   :width: 75%

 In this step you can also set the type of data and language of the data and you must add a license for the publication. The license can be selected through a built-in wizard. If you are not sure which license to choose, answer the questions on the top of the built-in wizard form to find the appropriate license.

  .. image:: ../img/license.png
   :align: center
   :width: 75%

 Click 'Next >>' to go to the second step of the online deposit workflow.

2. Next you must select a community, and optionally a collection and/or a metadata schema (if possible). If you are a member of a community and you want to deposit data in that community, select the community name. The available collections will be pre-populated based on which community you choose and which collections you have created yourself.

If a community or collection has a metadata schema attached, the corresponding form will be shown and all mandatory fields need to be filled in.

 .. image:: ../img/deposit-workflow-2.png
   :align: center
   :width: 75%

Click 'Next >>' to go to the third and final step of the online deposit workflow.

3. In this final step you can fill in optional information such as the embargo data of your data (if configured).

You can also specify links that are related to this publication. If you have any metadata that does not fit the basic or community metadata fields, you can add them here. For every field there needs to be a unique field name and a value.

Please carefully read the `Terms of use`_ and `Data Producer Agreement`_ before you agree by checking the checkbox.

 .. image:: ../img/deposit-workflow-3.png
   :align: center
   :width: 75%

When you have checked all metadata in the right sidebar, click on the **Complete** button to finalize your deposit.

.. _workflows-applications:

==============
Workflows and applications
==============

If you have many deposits to create, or have an automated workflow set up or application that generates data that needs to be published, you can make use of the REST API provided by the service. Please refer to the :ref:`REST API <rest-api>` page for more information.

.. Links:

.. _`File formats`: https://repository.surfsara.nl/docs/formats
.. _`Terms of Use`: https://repository.surfsara.nl/docs/terms
.. _`Data Producer Agreement`: https://repository.surfsara.nl/docs/data-producer
