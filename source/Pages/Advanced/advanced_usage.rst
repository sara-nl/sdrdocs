.. _advanced-usage:

***********
Advanced Usage
***********

This page provides information on the advanced usage of the data repository, such as Metadata schema definition, and community/group memberships. It also describes the online deposite workflow which is the steps that you take to deposit data on the Data Repository.

.. contents:: 
    :depth: 8


.. _metadata-schema:

=================
Metadata schema
=================

A metadata schema is a logical plan showing the relationships between metadata fields, normally through establishing rules for the use and management of metadata. Metadata schema makes sure that your deposit or collection has complete and understandable information attached to it. 
The first question to ask before making a metadata schema is: Is it necessary to create a new metadata schema? or are there already existing metadata schemas which can be adapted for use? We advice to reuse existing schemas. You can find here the `best practices for defining your metadata schema`_.

To define a metadata schema for your data, go to the profile tab of account overview page click on **Create new metadata schema** to go to the metadata schema creation form.


 .. image:: ../Screenshots/create_new_metadata_schema.png
   :align: center 


 
 You need to provide a title, creator, and description for the metadata schema. Then add metadata fields to the schema. Metadata field contains information about the field such as description, default value, type and if the field is optional or not. To save the field click on the **Save** icon under **Actions**. 
 In **Other options**, you can also specify if it is a public metadata schema. In the end hit **Create** button to finalise the creation of the metadata schema.


.. _collections:

=================
Collections
=================
Collection is a useful way to bundle a large number of deposits. Collections itself can also be bundle in another collection. Any structure is possible.

To create a new collection, go to the profile tab of the account overview page and click on **Create new collection** to go to the collection creation form. Provide the title, creator, description and optionally the parent collection of this collection object. Then hit **Create** to save your collection. The new collection will now be available during the online deposit
workflow.

  .. image:: ../Screenshots/create_new_collection.png
   :align: center 

To see the list of your current collections, go to your account page and then choose the **Collection** tab on the left.

.. _groups:

=======
Groups
=======

A group is a simple bundling of one or more users. They can be used to provide access or administrative privileges to a bunch of people using only a single relation.

To create a new group or to see the list of current groups are member of, go to your account page and then choose the **Groups** tab on the left. 

 .. image:: ../Screenshots/group_creation.png
   :align: center 


You can also create a group by going to the profile tab of account overview page click on **Create new group** to go to the group creation form. 

 .. image:: ../Screenshots/profile_group_creation.png
   :align: center 


A new page will be open where you need to provide name and description for the group, invite other members to join the group, and assign admins to the group. After you enter the information, click on the **Create** button.

  .. image:: ../Screenshots/create_new_group.png
   :align: center 


.. _communities:

==============
Communities
==============

Communities bundle collections and deposits under a single entity. With a community, you can add policies to deposits that make sure publications are up to the standards of your community.

To create a new group or to see the list of current groups are member of, go to your account page and then choose the **Communities** tab on the left. You can also create the community from the profile tab of your account overview page click on **Create new community** to go to the community creation form. 

  .. image:: ../Screenshots/community_creation.png
   :align: center 

A new page will be open where you need to provide more information about the new community you make such as the title, creator, and description. You should assign at least one member to the community. You can also choose who can be the administrators of the community. If you are a community administrator, you have special privileges regarding the reviewing of objects, and editing their metadata.
More information such as description, default collection and default metadata schema can be defined for the community. In the end you can choose the policies you want to apply to the community. After you enter the information, click **Create** to make the community.

  .. image:: ../Screenshots/create_new_community.png
   :align: center 

Your community is now created and will be available during the workflow of new deposits. It is also visible in the community tab of your account overview page

.. Links:

.. _`est practices for defining you metadata schema`: http://www.niso.org/apps/group_public/download.php/5271/N800R1_Where_to_start_advice_on_creating_a_metadata_schema.pdf
.. _`Handle Server`: http://hdl.handle.net/