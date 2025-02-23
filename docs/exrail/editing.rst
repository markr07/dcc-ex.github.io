.. include:: /include/include.rst
.. include:: /include/include-l1.rst
.. include:: /include/include-ex-r.rst
|EX-R-LOGO|

**********************
Editing myAutomation.h
**********************

|SUITABLE| |conductor| |tinkerer| |engineer| |support-button|

.. sidebar::
   :class: sidebar-on-this-page 

   .. contents:: On this page
      :depth: 4
      :local:

The instructions containing all your objects and sequences is added to your |EX-CS| by creating a file called `myAutomation.h` in the same folder as 'CommandStation-EX.ino'.

Connecting your Arduino and pressing the :guilabel:`Upload` button in the usual way will save the file and upload your script into the Command Station.

You can create and edit the `myAutomation.h` using a text editor (like Notepad), but if you are using the |Arduino IDE| (rather than the |EX-I|) you can create the myAutomation.h file in the |Arduino IDE|. Use the pulldown button and select New Tab (or simply press Ctrl+Shift+N).

.. image:: /_static/images/exrail/setup1.jpg
   :alt:  Setup pulldown button
   :align: center
   :scale: 100%
   :target: #myautomation-h-editing-your-sequences

.. image:: /_static/images/exrail/setup2.jpg
   :alt:  Setup pulldown menu
   :align: center
   :scale: 100%
   :target: #myautomation-h-editing-your-sequences

Enter the file name "myAutomation.h" (This is case sensitive)

.. image:: /_static/images/exrail/setup3.jpg
   :alt:  Setup myAutomation.h
   :align: center
   :scale: 100%
   :target: #myautomation-h-editing-your-sequences

And type your script in.

.. image:: /_static/images/exrail/setup4.jpg
   :alt:  Setup Example file
   :align: center
   :scale: 100%
   :target: #

|

Content
=======

What you will need to add to your `myAutomation.h`` file will be explained in the next few pages, but can be categorised as:

* :doc:`Objects </exrail/creating-elements>`
* :doc:`Commands </exrail/getting-started>`
* :doc:`Sequences </exrail/getting-started>`

----

Re-upload the EX-CommandStation software
========================================

Using EX-Installer
------------------

.. important::

   If you are using |EX-I| **DO NOT** create or edit the myAutomation.h file in the EX-Installer installation folder (the folder the EX-Installer creates).

   Instead, create you myAutomation.h anywhere else and point EX-Installer to that folder when it askes.

#. create your 'myAutomation.h' file in any ``CommandStation-EX``, anywhere on your computer (except the EX-Installer installation folder.)
#. Run |EX-I|
#. When asked, point EX-Installer to the folder and file that you created.

The myAutomation.h file will be automatically loaded with the |EX-CS| software.

See :doc:`/ex-installer/managing-config-files` for more information.

----

Using the Arduino IDE
---------------------

#. Place your 'myAutomation.h' file in the ``CommandStation-EX`` subfolder of wherever you extracted the |EX-CS| files from GitHub.
#. Run the |Arduino IDE|
#. Open the ``CommandStation-EX`` folder
#. Select the Board, COM port etc. as before
#. click :guilabel:`Upload`

The myAutomation.h file will be automatically loaded with the |EX-CS| software.

|HR-HEAVY|

Next Steps - Objects
====================

   
See the :doc:`creating-elements` page or click the 'Next' button to learn how to add the key objects you will need to create your automation sequences.