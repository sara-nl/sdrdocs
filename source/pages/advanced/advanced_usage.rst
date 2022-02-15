.. _advanced-usage:

********************
Advanced usage
********************

This page provides information on advanced usage of the SURF Data Repository, such as collection and group creation plus memberships.

.. contents::
    :depth: 8


.. _advanced-creating-collections:

=====================
Creating collections
=====================

For a complete description of collection objects, see :ref:`Collections <advanced-objects-collections>`.

To create a new collection, go to the profile tab of the account overview page and click on **Create new collection** to go to the collection creation form. Provide the necessary details and optionally set a parent collection. Then hit **Create** to create your collection. The new collection will now be available during the online deposit workflow.

.. image:: ../img/collection-form-1.png
  :align: center
  :width: 90%
  :alt: Collection form 1

To see a list of your current collections, go to your account page and then choose the **Collections** tab on the left.

.. _advanced-creating-groups:

=====================
Creating groups
=====================

For a complete description of group objects, see :ref:`Groups <advanced-objects-groups>`.

To create a new group or to see the list of current groups you are a member of, go to your account page and then choose the **Groups** tab on the left.

.. image:: ../img/account-groups.png
  :align: center
  :width: 90%
  :alt: Account groups

Click on the 'Create new group' button to start creating a new group.

A new page will be open where you need to provide name and description for the group.

.. image:: ../img/group-form-1.png
  :align: center
  :width: 90%
  :alt: Group form 1

You can add other members to the group, and assign administrators to the group on the tab 'Permissions'. After you enter the information, click on the **Create** button to create the group.

.. image:: ../img/group-form-2.png
  :align: center
  :width: 90%
  :alt: Group form 2

.. _advanced-api-tokens:

=================
API tokens
=================

The REST API can be used for interaction with Data Repository via external services or applications, for example for integration with other websites (research community portals) or for uploading or downloading large data sets that are not easily handled via a web browser. When requesting user-specific information through the REST API, an API access token is required. A token can be generated in your account page via the web interface. API tokens are for personal use only and should not be share publicly or with other persons.

Go to the **API tokens** tab on the left side of your account page to see an overview of all tokens you have generated. To create a new API token, enter a name and click on **Add API token** to generate a new token.

.. image:: ../img/account-tokens.png
  :align: center
  :width: 90%
  :alt: Account API tokens

.. _advanced-share-links:

=================
Share links
=================

Data sets that are not public or currently under embargo can be made accessible using share links that contain unique tokens. Share links are specific for a given object and can be generated on the landing page of an object using the share functionality (top-right corner). This can only be done by the owner or an administrator of the object or the community the object resides under.

.. image:: ../img/share-links.png
  :align: center
  :width: 90%
  :alt: Share links

A form will be shown that allows for some settings, including the expiration date of the link and whether it includes access to children objects and their files.

.. image:: ../img/share-links-form.png
  :align: center
  :width: 90%
  :alt: Share links form

Click on 'Until embargo' to set the expiration date to the embargo date of the object (if applicable). Click on 'Generate' to create the share token and link. It will be put on your system's clipboard and can be pasted in another application this way.

To see an overview of your share tokens, go to the account page and select the :ref:`Share links <account-sharelinks>` tab.

.. Links:

.. _`best practices for defining your metadata schema`: http://www.niso.org/apps/group_public/download.php/5271/N800R1_Where_to_start_advice_on_creating_a_metadata_schema.pdf
