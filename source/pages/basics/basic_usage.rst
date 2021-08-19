.. _basic-usage:

******************************
Navigating the data repository
******************************

This page provides information on the basic usage of the data repository, such as discovering, searching, and downloading data. For most of the functionality described on this page registration is not required.

.. contents:: Contents
    :depth: 2
    :local:


Homepage
========

.. sidebar::
   **Note:**

   **Deposit** is an object containing one or more files and corresponding metadata

   **Collection** is a bunch of deposits and/or collections and has metadata of its own

   **Community** is a group of common users that are part of a research domain or initiative

   See the :ref:`objects reference <advanced-objects>` for more information on object types.

On the homepage you can quickly find the latest deposits and collections, start depositing your own data, or search for existing digital objects for download.

The search bar can be used to quickly find deposits and collections. It supports faceted search by prepending a field (e.g. 'title') before your search term, for example 'title:data'.

Clicking on the avatar in the top right corner presents you with a dropdown menu where you can locate your account details. The 'My account' option sends you to your `account page`_. Here you can create and manage your deposits, collections, groups and, if allowed, communities and schemas. Please refer to the :ref:`advanced usage <advanced-usage>` section of the documentation for more information.

.. image:: ../img/homepage.png
   :align: center
   :width: 90%
   :alt: Home page

.. _search-data:

Search and discover datasets
============================
To search for data use the search functionality on the home page. Both registered and unregistered users can search for data. In the search bar you can enter keywords so search in the repository. These keywords any part of a title, keyword, abstract or any other metadata. To search only in a specific field, add the field name before the search term followed by a colon, e.g. `title:biology` or `publisher:SURF`.

 .. image:: ../img/search.png
   :align: center
   :width: 90%

Advanced searches can be performed by clicking the Search button and clicking "Advanced". The advanced search criteria allow to search only for specific objects like deposits, collections, schemas, communities or a combination of objects. It also allows to change the order of the search results by Title, Creator, Identifier, or Creation date and to search within a specific community.

 .. image:: ../img/search-advanced.png
   :align: center
   :width: 90%

.. note:: If you have the PID (Persistent Identifier) of the data you can directly search in the `Handle Server`_ and get the URL to the location of the data.

.. _deposit-landing-page:

Deposit landing page
====================
The landing page of a deposit is created after completion of the online deposit workflow. In the deposit landing page you can see the deposit's basic details, additional metadata and information about the status of the files in the deposit. From the deposit page it is possible to download individual files. Some files are marked as "offline", after logging in these files can be staged by clicking the "Request" button.

.. image:: ../img/deposit-landing-page.png
   :align: center
   :width: 90%
   :alt: Deposit landing page

.. _export-metadata:

Export Metadata
---------------

To export metadata of an object go to the object's landing page and click on the 'Export' dropdown button on the top-right corner of the page. You can choose different metadata format options here.

.. image:: ../img/deposit-landing-page-export.png
   :align: center
   :width: 90%
   :alt: Deposit landing page export

.. _download-zipped:

Download zipped archive
<<<<<<< HEAD
__________________________________
=======
-----------------------
>>>>>>> 692817e (Improve access links and headings)

You can download all files and optionally the metadata using the 'Download as' dropdown button and choosing 'ZIP'. Optionally you can also get a BagIt format archive file. Before downloading the deposit ensure that all files are "online", if some files are reported to be "offline" login and use the "Request" button to stage the files.

.. image:: ../img/deposit-landing-page-download.png
   :align: center
   :width: 90%
   :alt: Deposit landing page download

.. _deposit-citations:

Deposit citations
__________________________________

If you want to add a citation of the data set you can copy the provided text shown in the box at the bottom right in the right sidebar of the landing page. Click on the clipboard icon to copy the text to your clipboard.

Select a different citation style in the dropdown selection box to change it to the style you need.

.. _collection-landing-page:

Collection landing page
=======================
A landing page of a collection is similar to that of a deposit. In the collection landing page the basic details of the collection are listed, as well as all collections and deposits that are part of the collection.

.. image:: ../img/collection-landing-page.png
   :align: center
   :width: 90%
   :alt: Collection landing page

.. _collection-citations:

Collection citations
__________________________________

If you want to add a citation of the collection you can copy the provided text shown in the box at the bottom right in the right sidebar of the landing page. Click on the clipboard icon to copy the text to your clipboard.

Select a different citation style in the dropdown selection box to change it to the style you need.

.. _search-data:

==================================
Search and discover datasets
==================================

To search for data use the search functionality on the home page. The text entered can be part of a title, keyword, abstract or any other metadata.

Both registered and unregistered users can search for data. You can also make search within specific communities, which means the search results will be limited to that community.

.. image:: ../img/search.png
   :align: center
   :width: 90%
   :alt: Search

Advanced searches can be performed by clicking the Search button, then entering the additional search criteria on the page that is shown. You can set advanced search criteria to search for deposits, collections, schemas, communities or combinations of any of them. You can also order the search results by Title, Creator, Identifier, or Creation date.

.. image:: ../img/search-advanced.png
   :align: center
   :width: 90%
   :alt: Search advanced

.. sidebar::
    If you have the PID (Persistent Identifier) of the data you can directly search in the `Handle Server`_ and get the URL to the location of the data.


.. note:: If you have the PID (Persistent Identifier) of the data you can directly search in the `Handle Server`_ and get the URL to the location of the data.

.. Links:

.. _`account page`: https://repository.surfsara.nl/user
.. _`Handle Server`: http://hdl.handle.net/
