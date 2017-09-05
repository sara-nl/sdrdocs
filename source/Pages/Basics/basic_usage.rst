.. _basic-usage:

**************
Basic Usage
**************

This page provides information on the basic usage of the data repository. It also describes the online deposite workflow on the Data Repository.

.. contents:: 
    :depth: 4


.. _logging_in:

==================
Logging in
==================

Login with your user credentials in the `Login <https://tdr-test.surfsara.nl/user/login>`_ page of the Data Repository Service.

If you do not have access, go to [Obtaining Access](obtain-access) page for more information.



	


.. _homepage:

================
Homepage
================

After logging in to your account, you will be redirected to your homepage where you can quickly deposit or create collections of data.

**Deposit**

**Collection**On the right you can see the latest deposits an collection created on the data repository.	

.. _prepare_data:

===============================	
Preparing data
===============================

To prepare data for a deposit there are some best practices for the file format, file size, metadata, data documentation and organisation. For more information, visit the [Best Practices](best-practices.md) page.


.. _job-match:

==============
Depositing data
==============

To deposite data, you should login as a registered user. In the main page click on "Deposit now". Depositing data in Repository service is a 6 step process. 

.. code-block:: console

   $glite-wms-job-list-match -a simple.jdl # replace simple.jdl with your JDL file

Alternatively, use your delegation ID:

.. code-block:: console

   $glite-wms-job-list-match -d homer simple.jdl # replace homer with your delegation id, in this case your login name 
	
.. note:: The ``-a`` option should not be used frequently. It creates a proxy of your certificate 'on-the-fly' when the job is submitted; therefore ``-a`` is quite inefficient when submitting hundreds of jobs.

Your job is now ready. Continue to the next step to submit it to the Grid!

To submit your first Grid job and get an understanding of the job lifecycle, we will perform these steps:

* :ref:`Job submission <job-submit>`
* :ref:`Status tracking <job-status>`
* :ref:`Output retrieval <job-output>`

.. _job-submit:

==========================
Submit the job to the Grid
==========================

.. sidebar:: First Job explained

		.. seealso:: For more detailed information about submitting a simple Grid job, have a look at our mooc video :ref:`mooc-submit-job`.

You should have your ``simple.jdl`` file ready in your :abbr:`UI (User Interface)` up to this point. When you submit this simple Grid job to the :abbr:`WMS (Workload Management System)`, a job will be created and sent to a remote Worker Node. There it will execute the command ``/bin/hostname -f`` and write its standard output and its standard error in the ``simple.out`` and ``simple.err`` respectively.

* Submit the simple job by typing in your :abbr:`UI (User Interface)` terminal this command:

  .. code-block:: console

     $glite-wms-job-submit -d $USER -o jobIds simple.jdl

     Connecting to the service https://wms2.grid.sara.nl:7443/glite_wms_wmproxy_server
     ====================== glite-wms-job-submit Success ======================
     The job has been successfully submitted to the WMProxy
     Your job identifier is:

     https://wms2.grid.sara.nl:9000/JIVYfkMxtnRFWweGsx0XAA

     The job identifier has been saved in the following file:
     /home/homer/jobIds
     ==========================================================================

Note the use of ``-d $USER`` to tell your job that it should use your delegated proxy certificate.	
	
The option ``-o`` allows you to specify a file (in this case ``jobIDs``) to store the unique job identifier:

* You can use this URL identifier to monitor your job from the command line or your browser and to get the job output.
* Note that omitting the ``-o`` option means that the jobID is not saved in a file. When you do not save this id you will effectively loose the output of your job!

The jobID string looks like this:

.. code-block:: console

   $cat jobIds

    ###Submitted Job Ids### 
    https://wms2.grid.sara.nl:9000/JIVYfkMxtnRFWweGsx0XAA


.. _job-status:

====================
Track the job status
====================

To check the current job status from the command line, apply the following command that queries the :abbr:`WMS (Workload Management System)` for the status of the job. 

* After submitting the job, type:

  .. code-block:: console

     $glite-wms-job-status https://wms2.grid.sara.nl:9000/JIVYfkMxtnRFWweGsx0XAA #replace with your jobID

* Alternatively, if you have saved your jobIds into a file you can use the ``-i`` option and the filename as argument:

  .. code-block:: console

     $glite-wms-job-status -i jobIds

* Finally, a third (optional) way to check the job status is with the web browser in which :ref:`you installed your certificate <digicert_browser_install>`. In this browser open the jobID link:

	https://wms2.grid.sara.nl:9000/JIVYfkMxtnRFWweGsx0XAA #replace with your jobID

Note that the URL can only be accessed by you as you are authenticated to the server with the certificate installed in this browser. If your certificate is not installed in this browser, you will get an authentication error.


.. _job-cancel:

Cancel job
==========

* If you realize that you need to cancel a submitted job, use the following command:

  .. code-block:: console

     $glite-wms-job-cancel https://wms2.grid.sara.nl:9000/JIVYfkMxtnRFWweGsx0XAA #replace with your jobID

* Alternatively, you can use the ``jobIds`` file:

  .. code-block:: console

     $glite-wms-job-cancel -i jobIds


.. _job-output:

===================
Retrieve the output
===================

The output consists of the files included in the ``OutputSandbox`` statement. You can
retrieve the job output once it is successfully completed, in other words the
job status has changed from ``RUNNING`` to ``DONE``. The files in the
output sandbox can be downloaded for approximately one week after the job finishes.

.. note:: 
        You can choose the output directory with the ``--dir`` option. If you do not use this option then the output will be copied under the :abbr:`UI (User Interface)` ``/scratch`` directory with a name based on the ID of the job.  

* To get the output, type:

  .. code-block:: console

     $glite-wms-job-output https://wms2.grid.sara.nl:9000/JIVYfkMxtnRFWweGsx0XAA #replace with your jobID
	
* Alternatively, you can use the jobIDs file:
	
  .. code-block:: console

     $glite-wms-job-output --dir . -i jobIds

where you should substitute ``jobIds`` with the file that you used to store the
job ids.

If you omitted the ``--dir`` option, your output stored on the
``/scratch`` directory on the :abbr:`UI (User Interface)`. Please remove your files from the
``/scratch`` directory when they are no longer necessary. Also keep in
mind that if the ``/scratch`` directory becomes too full, the
administrators remove the older files until enough space is available
again.

Check job output
================

* To check your job output, browse into the downloaded output directory. This includes the ``simple.out``, ``simple.err`` files specified in the ``OutputSandbox`` statement:

  .. code-block:: console

	$ls -l /home/homer/homer_JIVYfkMxtnRFWweGsx0XAA/

	-rw-rw-r-- 1 homer homer  0 Jan  5 18:06 simple.err
	-rw-rw-r-- 1 homer homer 20 Jan  5 18:06 simple.out

	$cat /home/homer/homer_JIVYfkMxtnRFWweGsx0XAA/simple.out # displays the hostname of the Grid worker node where the job landed
	wn01.lsg.bcbr.uu.nl

==================
Recap & Next Steps
==================
        
Congratulations! You have just executed your first job to the Grid!

Let's summarise what we've seen so far.

You interact with the Grid via the :abbr:`UI (User Interface)` machine ``ui.grid.sara.nl``. You describe each job in a JDL (Job Description Language) file where you list which program should be executed and what are the worker node requirements. From the :abbr:`UI (User Interface)`, you create first a proxy of your Grid certificate and submit your job with ``glite-*`` commands. The resource broker, called WMS (short for Workload Management System), accepts your jobs, assigns them to the most appropriate CE (Computing Element), records the jobs statuses and retrieves the output.

This is a short overview of the commands needed to handle simple jobs: 

+---------------------+--------------------------------------------------------+
| startGridSession    | ``startGridSession lsgrid``                            |
+---------------------+--------------------------------------------------------+
| submit job          | ``glite-wms-job-submit -d $USER -o jobIds simple.jdl`` |	    
+---------------------+--------------------------------------------------------+
| job status          | ``glite-wms-job-status -i jobIds``                     |	   
+---------------------+--------------------------------------------------------+
| cancel job          | ``glite-wms-job-cancel -i jobIds``                     |
+---------------------+--------------------------------------------------------+
| retrieve job output | ``glite-wms-job-output --dir . -i jobIds``             |
+---------------------+--------------------------------------------------------+


.. seealso:: Try now to port your own application to the Grid. Check out the :ref:`best-practices` section and run the example that suits your use case. The section :ref:`advanced` will help your understanding for several Grid modules used in the :ref:`best-practices`. 

	Done with the :ref:`basics`, but not sure how to proceed? We can help! Contact us at helpdesk@surfsara.nl.


.. Links:

.. _`Grid WMS animation`: http://web.grid.sara.nl/mooc/animations/wms.html
.. _`Grid job status animation`: http://web.grid.sara.nl/mooc/animations/wms_with_status.html 
