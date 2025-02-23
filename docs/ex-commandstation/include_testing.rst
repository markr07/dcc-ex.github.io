.. include:: /include/include.rst
.. include:: /include/include-l1.rst
.. include:: /include/include-ex-cs.rst
.. meta::
   :keywords: Testing

|EX-CS-LOGO|

***************
Test Your Setup
***************

|SUITABLE| |conductor| |tinkerer| |engineer| |support-button|

.. sidebar::
   :class: sidebar-on-this-page

   .. contents:: On this page
      :depth: 3
      :local:

This page is specifically intended for a |conductor-text| or |tinkerer-text| who has either:

- Purchased a ready-to-run (RTR) |EX-CSB1|, or 
- Assembled *just* the recommended do-it-yourself (DIY) hardware (including WiFi). 

However it will generally be suitable for testing most other configuration options.

Testing control of a loco
=========================

You need to test with a locomotive equipped with a DCC decoder (either a standard or sound decoder). Ideally, it should be a loco already proven to work on DCC. Otherwise, if you have a problem, you may not be able to tell if the problem is the decoder or the |EX-CS|.

There are two simple options for testing your setup described below:

* Using our |EX-WT| (recommended)
* using the |Engine Driver| app installed on an Android device, |BR| or the |WiThrottle| app installed on an iOS device

Using EX-WebThrottle
--------------------

.. figure:: /_static/images/throttles/webthrottle_setup.png
   :alt: EX-WebThrottle
   :align: center
   :scale: 40%

   EX-WebThrottle setup

.. sidebar:: 

    |tinkerer| |engineer| |BR| Additional options (throttles) for testing and diagnosing issues are available and is described in the :doc:`/ex-commandstation/advanced-setup/controllers` page if needed .

Connect Everything:

* Disconnect the |EX-CS| from the computer (that you used to load the software)
* Connect wires from the MAIN Terminals of the motor driver (output A) to your **MAIN track**
* Plug in the power supply for the motor driver **only**
* Reconnect the |EX-CS| to the computer
* Wait for about 30 seconds for the Command Station to run through its startup sequence

.. important:: 

   The programming track is for programming only. Make sure you are on the MAIN track if you expect your loco to move or respond to light or sound commands.

.. figure:: /_static/images/installer/exwebthrottle.jpg
   :alt: EX-WebThrottle
   :scale: 80%

   EX-WebThrottle screen

* Click this link and it will load a web page from our server that will run the web throttle on your PC

.. rst-class:: dcclink

   `Run EX-WebThrottle Now <https://DCC-EX.github.io/WebThrottle-EX>`_ |EXTERNAL-LINK|

* Click on the "Serial" dropdown button and select "Serial"
* Click on the :guilabel:`Connect EX-CS` button 
* If the program finds a compatible device,

  * It will open a popup a window showing you a selection. |BR| It may show a line at the top such as "Arduino Mega 2560 (COM3)". (The COM port will vary)
  * Click on your board to select it
  * Then click the :guilabel:`Connect EX-CS` button
  
* You should then be connected to the |EX-CS| and should see the response from the Command Station in the log textbox of the debug console at the bottom of the throttle window. |BR| Make sure your debug console is open. If it isn't, use the slider button in the lower left to open it. You can also open the DevTools window in your browser to see more developer logging
* Once you are connected, you can:   
  
  * Enter the ``<s>`` command in the "direct command" textbox to get status information from your Command Station. To do this just enter ``s`` (without the quotes) and press the SEND button. 
  * You should see <iDCC++...> returned in the log window with your version, type of Arduino, type of motor driver, and some other information |BR| |BR|

* Now you are ready to run trains! |BR| |BR|
* Place your loco on the **MAIN track**, a loco will NOT run on a programming track 
* Click the :guilabel:`Power Slider` button to turn on power to your track
* You should see lights on your |Standard Motor Driver| or |EX-MS| and an indication that your loco has power
* Next go to the ``Locomotive ID`` textbox 
* Enter the DCC address of your loco
* Then press the :guilabel:`Acquire` button
* You should now have full control over your loco
* The circular control or vertical slider (chosen by the throttle select slider) can be moved by clicking and holding down the mouse button and dragging, clicking at a spot where you want the throttle to move, or clicking the + and - buttons

.. note:: 
   If you did not see the LEDs light up, near the A and B outputs on the |Motor Shield|, try pushing down on the |motor shield| to make sure that the pins are properly seated into the Arduino. If that did not work, scroll down to the very bottom of this page and click on the 'Next' button for troubleshooting help.

.. sidebar:: Progressive Web App (PWA)

    |EX-WT| is also a Progressive Web App (PWA). That means you can install it on your computer and run it right from your start menu! If you go into the |EX-WT| settings panel (click the 3 line "hamburger menu" at the top left), you will find a "Settings" menu. Click on "Apps" and then select "Install as an App". You can now work offline and always find |EX-WT| with your other Apps!

Click this link: :doc:`EX-WebThrottle </ex-webthrottle/index>` to run |EX-WT| hosted on our site, or visit `GitHub <https://github.com/DCC-EX/WebThrottle-EX>`_ |EXTERNAL-LINK| to get the latest version to run on your computer.

|force-break|

Using Engine Driver or WiThrottle - Requires WiFi
-------------------------------------------------

.. important:: 
   :class: important-float-right

   The programming track is for programming only. Make sure you are on the MAIN track if you expect your loco to move or respond to light or sound commands.

Connect Everything:

* Disconnect the |EX-CS| from the computer (that you used to load the software)
* Connect the wires from the 'MAIN' terminals of the |motor shield| (output A) to your MAIN track
* If you are using a |EX-CSB1-SHORT|, plug in your single power supply to the board
* If you are using a |EX-MS|, plug in your single power supply to the shield
* If you are using a |standard Motor Driver|, plug in the two power supplies (The one for the Arduino and the one for the |motor shield|). Make sure to not plug the higher voltage power supply into the Arduino by mistake
* Wait for about 30 seconds for the Arduino to run through the initial startup sequence

.. figure:: /_static/images/throttles/throttle_wifi_direct.png
   :alt:  WiFi Throttle Direct to CS
   :align: center
   :scale: 40%

   WiFi Throttle Direct to Command Station

Using Engine Driver (Android)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: /_static/images/installer/engine_driver.png
   :align: right
   :alt: Engine Driver
   :scale: 80%

   Engine Driver

You will need to install |Engine Driver| on your mobile device and then connect to the |EX-CS|, either directly with AP mode or through your router with Station Mode. You can then use your phone to control your trains.

* If you have set up your |EX-CS| in |Access Point Mode| (The Recommended approach)
  
  * Open the network settings on you phone
  * Disconnect from your normal network and change to the network of the |EX-CS|
  
    * SSID (Network name): ``DCCEX_xxxxxx`` |BR| where the x's are the last 6 digits of your device' MAC address (unique to each device)
    * Password: ``PASS_xxxxxx`` |BR| where the x's are the last 6 digits of your device' MAC address (same as above)

* If you have set up your |EX-CS| in |Station Mode| (The alternate approach)
  
  * open the network settings on you phone
  * change to your home network
  
    * Use your normal home SSID (Network name) and Password to connect to the network 

.. note:: 
   :class: note-float-right

   If you have any difficulties check the :doc:`/support/ex-cs-troubleshooting` page for assistance.

* Start the |engine driver| App
* Go through the initial startup pages to set some basic configuration items
* On the 'Connection screen'
  
  * You should see ``DCCEX_xxxxxx`` (as above) in the discovered servers list
  * Click on this. |BR| (As long as you did not change the IP address of the |EX-CS| when you ran |EX-I| then this should connect

* You should now be on the the 'Throttle screen'

* Turn on the power to the track via the Menu 
   
   * (The three dots or bars) then 'Power'.  Then click the :guilabel:`Power` button till it goes green. (may require more than one click)
   * The four red LEDs on the Motor board will turn on
   * Click :guilabel:`Back`

* Back on the 'Throttle screen'

  * Click one of the :guilabel:`Select` buttons
  
* This will have taken you to the 'Select Loco screen'

  * Enter the DCC Address of the loco you put on the track
  * Select ``Short`` or ``Long`` (normally if the address is less than 127, it will automatically assume it is short) 
  * Click :guilabel:`Aquire`

* Back on the 'Throttle screen' you can now use the sliders to move your train on the MAIN track.

See :doc:`Engine Driver Page </throttles/software/engine-driver>` for details on how to install and run |Engine Driver|.

.. note:: 
   If you did not see the LEDs near the A and B outputs light on the |Motor Shield|, try pushing down on the |motor shield| to make sure that the pins are properly seated into the Arduino. If that did not work, scroll down to the very bottom of this page and click on the 'Next' button for troubleshooting help.

Using WiThrottle (Apple iOS)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. note:: 
   :class: note-float-right

   If you have any difficulties check the :doc:`/support/ex-cs-troubleshooting` page for assistance.

* If you have set up your |EX-CS| in |Access Point Mode| (The Recommended approach)
  
  * Open the network settings on you phone
  * Change to the network of the |EX-CS|
  
    * SSID (Network name) : ``DCCEX_xxxxxx`` |BR| where the x's are the last 6 digits of your device' MAC address (unique to each device)
    * Password: ``PASS_xxxxxx`` |BR| where the x's are the last 6 digits of your device' MAC address (same as above)

* If you have set up your |EX-CS| in |Station Mode| (The alternate approach)
  
  * Open the network settings on you phone
  * Change to your home network
  
    * Use your normal home SSID (Network name) and Password to connect to the network  

* Start the |WiThrottle| App
* |WiThrottle| will try to find the |WiThrottle Server| on the |EX-CS|

  * If you are using |Access Point Mode| 

    * It will *not* find the |WiThrottle Server| automatically
    * You must enter:

      * The IP Address: ``192.168.4.1``
      * The Port: ``2560``

    * |WiThrottle| should then connect 

  * If you are using |Station Mode| 
  
    * It should find the |WiThrottle Server| and automatically connect to it

.. important:: 
   :class: important-float-right

   |WiThrottle Lite| (the free version) does not have the ``Track Power`` function. You will either a) you need to purchase the full version, b) configure the power to turn on in |EX-I|, or c) you can :doc:`add a startup command </ex-commandstation/advanced-setup/startup-config>`.

* You should then see the 'Address Screen'
* Turn the track power on by selecting the 'settings' tab and clicking on the ``Track Power``

   * The four red LEDs on the Motor board will turn on

* Go back to the 'Address' tab
* Enter the DCC Address of the loco you put on the track in the ``Keypad`` field
* Select ``Long`` or ``Short`` (normally if the address is less than 127, it should be a 'Short' address.)
* Click the :guilabel:`Set` button
* The address should appear in the green box at the top left.
* Select the 'Throttle' tab
* You can now use the sliders to move your train on the MAIN track

See :doc:`WiThrottle Page </throttles/software/withrottle>` for details on how to install and run |WiThrottle|.

.. important:: 

   **Locos Can't Respond to Throttle Commands on the Programming Track!**

   We have repeated this in multiple places on the Website because it is such a common issue. The MAIN track is for running trains, the PROG (service track) is for programming your loco. **THE LOCO CANNOT RESPOND TO THROTTLE OR FUNCTION COMMANDS WHILE ON THE PROG TRACK** This is by design and part of the NMRA DCC specification.

|HR-HEAVY|

Next Steps - Run Your Trains
============================

*You now should have everything you need to run your trains.*

We suggest that you look at the :doc:`/big-picture/index` to get some additional guidance on running trains and the additional capabilities of |DCC-EX| that you may prove of interest.

You might also like to look at the other :doc:`Throttles (Controllers) </ex-commandstation/advanced-setup/controllers>` that are available.

If you are still having difficulties click :guilabel:`Next` below.
