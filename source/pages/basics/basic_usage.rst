.. _basic-usage:

***********
Basic Usage
***********

This page provides information on the basic usage of the data repository, such as depositing data, searching data and downloading data. It also describes the online deposite workflow which is the steps that you take to deposit data on the Data Repository.

.. contents::
    :depth: 8


.. _log-in:

===========
Logging in
===========

Login with your user credentials in the `Login`_ page of the Data Repository Service.

If you do not have access, go to :ref:`How to get access <get-access>` page for more information.



.. _homepage:

================
Homepage
================

After you login to your account, you will be redirected to your homepage where you can quickly deposit data, find data to download or create collections of data.

.. sidebar::
    **Note:**

    **Deposit** is an object containing one or more files and corresponding metadata

    **Collection** is a bunch of deposits

On the right column you can see the latest deposits and collections that are uploaded on the data repository.

On the top left you see some statistics of your account such as the number of deposits and collections you have. "Show account detail" redirects you to your profile page.

On the buttom left column, the are  shortcuts for defining new collections, metadata schemas and groups, explained more in the :ref:`Advanced usage <advanced-usage>`.

 .. image:: ../img/homepage.png
   :align: center
   :width: 75%

.. _deposit-data:

==============
Deposit data
==============

Deposit is the act of uploading data to the Data Repository. Only registered users are permitted to deposit new records.


.. _prepare-data:

Prepare data
______________

 Before you make any deposits, you should make sure that your data has the right format. To prepare data for a deposit there are some best practices for the file format, file size, metadata, data documentation and organisation. For more information, visit the :ref:`Best Practices <best-practices>` page.

.. _deposit-workflow:

Deposit workflow
_________________

 Clicking the deposit link in the main interface opens the first of a three stage process required to upload data. The steps are as follows:

1. In the Create a new deposit page, select files to deposit and then click on Upload to upload the file.

 .. note:: Make sure that you are uploading an acceptable file format. Valid file extensions are: .jpg, .jpeg, .gif, .png, .txt, .text, .md, .pdf, .odt, .ods, .odp, .mp4, .avi, .hdf5, .h5, .hdf4, .nc, .cdl. If the data format you are trying to upload is not supported, you can always contact us for support.


 Then provide the basic metadata for your file such as Title, Creator, keywords (for searching purposes) and Description. The fields with a * are mandatory fields.

 .. image:: ../img/deposit1.png
   :align: center
   :width: 75%

 In this step you should also select the type of data and language of the data and a license for ypublication. The license can be selected through a built-in wizard. If you are not sure which license to choose, answer the questions on the top of the built-in wizard form to find the appropriate license. If your data is completely open to the public, no license is needed and this field can be skipped.

  .. image:: ../img/license.png
   :align: center
   :width: 75%

2. Next you can optionally select a community, collection and/or metadata schema. If you are a memeber of a community and you want to deposit data in that community, select the community name. The collection and metadata schema will be prepopulated based on which community you choose. If you are not member of any communities, you will see the collections and schemas defined by yourself. This step is optional and can be skipped. In the right you can the basic metadata you defined for the deposit.

 .. image:: ../img/deposit2.png
   :align: center
   :width: 75%

3. Finally you can fill in optional information about privacy settings on your data such as Embargo and end publication date. You can also specify links that are related to this publication. Please read the terms of use and agree with that by checking the checkbox before depositing data. In the end, click on the **Complete** button to finalize your deposit.

 .. image:: ../img/deposit3.png
   :align: center
   :width: 75%

.. _deposit-landing-page:

==============
Deposit landing page
==============
Deposit landing page is created after each deposit. In the deposit landing page you can see the deposit description, metadata and more information about the status of the data, for example if the data is online (on disk) or offline (on tape).

 .. image:: ../img/landing-page.png
   :align: center
   :width: 75%

.. _search-data:

====================
Search and discover datasets
====================
To search for data use the search functionality on the home page. The text entered can be part of a title, keyword, abstract or any other metadata.
Both registered and unregistered users can search for data. Unregistered users can only search for data sets that are publicly accessible.
You can also make search within specific communities, which means the search results will be limited to that community.

 .. image:: ../img/search.png
   :align: center
   :width: 75%

Advanced searches can be performed by clicking the Search button, then entering the additional search criteria on the page that is shown. You can set advanced search criteria to search for deposits, collections, schemas, communities or combinations of any of them. You can also order the search results by Title, Creator, Identifier, or Creation date.

.. sidebar::
    If you have the PID (Persistent Identifier) of the data you can directly search in the `Handle Server`_ and get the url to the location of the data.
   :align: center


.. note:: If you have the PID (Persistent Identifier) of the data you can directly search in the `Handle Server`_ and get the url to the location of the data.

.. _download-data:

==========================
Download data
==========================

To download data from the Data Repository you have to be logged in as a registered user. Unregistered users can only download data sets that are publically accessible.


To download data you should first go to the deposit landing page.
You can download single files by selecting the file you want to download and then clicking on the **download** link. If the data is **offline**, it means that the data is currently on tape. You should first request the data to be staged from the tape by clicking the **request** link.

To download several files at the same time, your can add the files to your basket and then download them all at once.

 .. image:: ../img/landing-page.png
   :align: center
   :width: 75%

.. _export-metadata:

==========
Export Metadata
==========

To export metadata you should first find the data by search. Then  go to the landing page of the data and click on the export link on the top-right corner of the metadata pannle. You can choose to export all the meta data or based on other criteria such as dublin core or community specific metadata.

 .. image:: ../img/export-metadata.png
   :align: center
   :width: 75%

.. Links:

.. _`Login`: https://repo-test.surfsara.nl/user/login
.. _`Handle Server`: http://hdl.handle.net/