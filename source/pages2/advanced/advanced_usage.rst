.. _advanced-usage:

***********
Advanced Usage
***********

This page provides information on the advanced usage of the data repository, such as Metadata schema definition, and community/group memberships. It also describes the online deposite workflow which is the steps that you take to deposit data on the Data Repository.

.. contents::
    :depth: 8


.. _account-overview:

=================
Account overview
=================
The account overview page provides an overview of the number of deposits and collections you have, also the number of groups and communities you are part of. From your account, there are links to quick actions for advanced functionalities such as creating a new  metadata schema, creating new groups and creating new communitites. Each of these will be explained in more detail in the following sections.

On the left side of your account overview page there are links to different parts of your account such as your profile, deposits, collections, groups, communities, messages, ... . Some other options are:
 - **Administrator:** shows an overview of all the items you currently have administrative rights to.
 - **Basket:** An overview of all the items you currently have in your basket. You can chose any item to download or remove from your basket. The Basket functionality is very useful if you want to download a bunch of individual object (or files). Go to the landing page of an object to add it to your basket.
 - **Favorites:** An overview of all the items you currently have marked as favourite. Click on the title of a favourite to go to the landing page, or the cross to remove the item from your list. To add an object to your favourites, go to the corresponding landing page and add it.

 .. image:: ../img/account_overview_page.png
   :align: center
   :width: 75%

.. _metadata-schema:

=================
Metadata schema
=================

A metadata schema is a logical plan showing the relationships between metadata fields, normally through establishing rules for the use and management of metadata. Metadata schema makes sure that your deposit or collection has complete and understandable information attached to it.
The first question to ask before making a metadata schema is: Is it necessary to create a new metadata schema? or are there already existing metadata schemas which can be adapted for use? We advice to reuse existing schemas. You can find here the `best practices for defining your metadata schema`_.

To define a metadata schema for your data, go to the profile tab of account overview page click on **Create new metadata schema** to go to the metadata schema creation form.


 .. image:: ../img/create_new_metadata_schema.png
   :align: center
   :width: 75%


 You need to provide a title, creator, and description for the metadata schema. Then add metadata fields to the schema. Metadata field contains information about the field such as description, default value, type and if the field is optional or not. To save the field click on the **Save** icon under **Actions**.
 In **Other options**, you can also specify if it is a public metadata schema. In the end hit **Create** button to finalise the creation of the metadata schema.


.. _collections:

=================
Collections
=================
Collection is a useful way to bundle a large number of deposits. Collections itself can also be bundle in another collection. Any structure is possible.

To create a new collection, go to the profile tab of the account overview page and click on **Create new collection** to go to the collection creation form. Provide the title, creator, description and optionally the parent collection of this collection object. Then hit **Create** to save your collection. The new collection will now be available during the online deposit
workflow.

  .. image:: ../img/create_new_collection.png
   :align: center
   :width: 75%

To see the list of your current collections, go to your account page and then choose the **Collection** tab on the left.

.. _groups:

=======
Groups
=======

A group is a simple bundling of one or more users. They can be used to provide access or administrative privileges to a bunch of people using only a single relation.

To create a new group or to see the list of current groups are member of, go to your account page and then choose the **Groups** tab on the left.

 .. image:: ../img/group_creation.png
   :align: center


A new page will be open where you need to provide name and description for the group, invite other members to join the group, and assign admins to the group. After you enter the information, click on the **Create** button.

  .. image:: ../img/create_new_group.png
   :align: center


.. _communities:

==============
Communities
==============

Communities bundle collections and deposits under a single entity. With a community, you can add policies to deposits that make sure publications are up to the standards of your community.

To create a new group or to see the list of current groups are member of, go to your account page and then choose the **Communities** tab on the left. You can also create the community from the profile tab of your account overview page click on **Create new community** to go to the community creation form.

  .. image:: ../img/community_creation.png
   :align: center
   :width: 75%

A new page will be open where you need to provide more information about the new community you make such as the title, creator, and description. You should assign at least one member to the community. You can also choose who can be the administrators of the community. If you are a community administrator, you have special privileges regarding the reviewing of objects, and editing their metadata.
More information such as description, default collection and default metadata schema can be defined for the community. In the end you can choose the policies you want to apply to the community. After you enter the information, click **Create** to make the community.

  .. image:: ../img/create_new_community.png
   :align: center
   :width: 75%

Your community is now created and will be available during the workflow of new deposits. It is also visible in the community tab of your account overview page

.. _api-token:

=================
API tokens
=================
Te HTTP REST API can be used for interacting with Data Repository via external services or applications, for example for integrating with other web-sites (research community portals) or for uploading or downloading large data sets that are not easily handled via a web browser.

Go to the **API tokens** on the left side of your account page to see an overview of all tokens you have generated for accessing this service externally through the REST API. To create a new API token, enter a name and click on **Add API token** to generate a new token.

  .. image:: ../img/api_token.png
   :align: center
   :width: 75%

.. Links:

.. _`best practices for defining you metadata schema`: http://www.niso.org/apps/group_public/download.php/5271/N800R1_Where_to_start_advice_on_creating_a_metadata_schema.pdf
