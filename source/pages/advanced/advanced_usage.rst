.. _advanced-usage:

***********
Advanced Usage
***********

This page provides information on the advanced usage of the data repository, such as Metadata schema definition, and community/group memberships. It also describes the online deposite workflow which is the steps that you take to deposit data on the Data Repository.

.. contents::
    :depth: 8


.. _collections:

=================
Collections
=================
A collection is a bundle of a (large) number of deposits and/or collections. Collections allow to create structure in your publications and make your data easier to understand and find. Collection are annotated using similar metadata as deposits.

To create a new collection, go to the profile tab of the account overview page and click on **Create new collection** to go to the collection creation form. Provide the necessary details and optionally set a parent collection. Then hit **Create** to create your collection. The new collection will now be available during the online deposit workflow.

  .. image:: ../img/collection-form-1.png
   :align: center
   :width: 75%

To see a list of your current collections, go to your account page and then choose the **Collections** tab on the left.

.. _groups:

=======
Groups
=======

A group is a bundling of one or more users. They can be used to provide access or administrative privileges to a bunch of people using only a single relation.

To create a new group or to see the list of current groups you are a member of, go to your account page and then choose the **Groups** tab on the left.

 .. image:: ../img/account-groups.png
   :align: center

Click on the 'Create new group' button to start creating a new group.

A new page will be open where you need to provide name and description for the group.

  .. image:: ../img/group-form-1.png
   :align: center

You can add other members to the group, and assign administrators to the group on the tab 'Permissions'. After you enter the information, click on the **Create** button to create the group.

  .. image:: ../img/group-form-2.png
   :align: center

.. _metadata-schema:

=================
Metadata schema
=================

A metadata schema is a logical plan showing the relationships between metadata fields, normally through establishing rules for the use and management of metadata. Metadata schema makes sure that your deposit or collection has complete and understandable information attached to it.

The first question to ask before making a metadata schema is: Is it necessary to create a new metadata schema? or are there already existing metadata schemas which can be adapted for use? We advice to reuse existing schemas. You can find here the `best practices for defining your metadata schema`_.

To define a metadata schema for your data, go to the account overview page and click on the **Metadata schemas** tab on the left. Hit the **Create new metadata schema** button to go to the metadata schema creation form.

 .. image:: ../img/account-schemas.png
   :align: center
   :width: 75%

You need to provide a title, creator, and description for the metadata schema:

 .. image:: ../img/schema-form-1.png
   :align: center
   :width: 75%

Then add metadata fields to the schema on the tab 'Fields'. A metadata field contains information about the field such as description, default value, type and if the field is optional or not.

 .. image:: ../img/schema-form-2.png
   :align: center
   :width: 75%

 To save the field click on the **Save** icon under **Actions**. You can move a field up or down in position by using the arrow buttons after each field.

 On the 'Permissions' tab you can add administrators who can also manage the schema.

 .. image:: ../img/schema-form-3.png
   :align: center
   :width: 75%

 Once satisfied hit the **Create** button to finalise the creation of the metadata schema. Please note that all schemas are public and can be used by any user.

.. _communities:

==============
Communities
==============

Communities bundle collections and deposits under a single entity. With a community, you can add policies to deposit workflows that make sure publications are up to the standards of your community.

To create a new community or to see the list of current communities you own or are a member of, go to your account page and then choose the **Communities** tab on the left. Hit the **Create new community** to go to the community creation form.

  .. image:: ../img/account-communities.png
   :align: center
   :width: 75%

You can also create the community from the profile tab of your account overview page click on **Create new community** to go to the community creation form. A new page will be open where you need to provide more information about the new community you make such as the title, creator, and description:

  .. image:: ../img/community-form-1.png
   :align: center
   :width: 75%

More information such as description, default collection and default metadata schema can be defined for the community on the 'Relationships' tab:

  .. image:: ../img/community-form-2.png
   :align: center
   :width: 75%

 On the 'Policies' tab you can choose the policies you want to apply to the community.

 .. image:: ../img/community-form-3.png
   :align: center
   :width: 75%

If you have a closed-member community, you should assign at least one member to the community on the 'Permissions' tab. Here you can also choose who can be the administrators of the community. If you are a community administrator, you have special privileges regarding the reviewing of objects, and editing their metadata:

 .. image:: ../img/community-form-5.png
   :align: center
   :width: 75%

After you enter the information, click **Create** to make the community.

Your community is now created and will be available during the workflow of new deposits. It is also visible in the community tab of your account overview page

.. _api-token:

=================
API tokens
=================
Te HTTP REST API can be used for interacting with Data Repository via external services or applications, for example for integrating with other web-sites (research community portals) or for uploading or downloading large data sets that are not easily handled via a web browser. When requesting user-specific information through the API, an access token is required. A token can be generated in your account page.

Go to the **API tokens** tab on the left side of your account page to see an overview of all tokens you have generated. To create a new API token, enter a name and click on **Add API token** to generate a new token.

  .. image:: ../img/account-tokens.png
   :align: center
   :width: 75%

.. Links:

.. _`best practices for defining your metadata schema`: http://www.niso.org/apps/group_public/download.php/5271/N800R1_Where_to_start_advice_on_creating_a_metadata_schema.pdf
