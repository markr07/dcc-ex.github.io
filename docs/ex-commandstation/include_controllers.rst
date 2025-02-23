.. include:: /include/include.rst
.. include:: /include/include-l1.rst
.. include:: /include/include-throttles.rst

|EX-CS-LOGO|

*********************************
Choosing a Throttle (Controller)
*********************************

|SUITABLE| |conductor| |tinkerer| |engineer| |support-button|

.. sidebar::
   :class: sidebar-on-this-page

   .. contents:: On this page
      :depth: 2
      :local:

This page is specifically intended for a |conductor-text| or |tinkerer-text| who has either:

- Purchased a ready-to-run (RTR) |EX-CSB1|, or 
- Assembled *just* the recommended do-it-yourself (DIY) hardware (including WiFi). 

If you are a |tinkerer-text| or |engineer-text| or have installed some of the additional, or different, hardware from that recommended for a |conductor-text| then we suggest that you look at the :doc:`/ex-commandstation/advanced-setup/controllers` page for the full list of Throttle (Controller) options.

----

What You Need & Why You Need It
===============================

You need just two things that work together to operate your model railroad:

* The |EX-CS| (aka the Command Station or 'CS')
* A Controller (aka Front-end, Cab, or Throttle)

The EX-CommandStation
---------------------

The |EX-CS| is explained in detail in the :doc:`/ex-commandstation/index` pages. It is either an |EX-CSB1| or an Arduino microcontroller with a motor driver and a WiFi shield. 

The Command Station accepts instructions from a controller and generates packets that are transmitted to your track and subsequently your trains.

The Throttle (Controller)
-------------------------

Since the |EX-CS| simply accepts commands to turn into signals for your layout, you need something that sends those commands to run your trains - a controller. (It isn't very practical to type something like <t 1 3 75 1> into a serial monitor to tell your train to move each time! 😉)

A controller can be a hardware device like a handheld throttle (also called a Controller or Cab), an App that runs on your phone, a Web Page, or front-end software like |JMRI| or Rocrail that runs on a computer or Raspberry Pi. 

----

Throttle (Controller) Options
=============================

.. sidebar:: Connection Types

   Your throttle (controller) can connect to the |EX-CS| several different ways, such as:

   * **WiFi**
   * **Direct connection using a USB cable**
   * 2 wires to an Arduino serial port
   * Ethernet
   * Bluetooth 
   * Remote connection (VNC, MQTT, etc.)

   You are welcome to explore the many other :doc:`/throttles/index`, but the the ones on this page are still recommended for initial testing. 

Here is a small subset of the throttles you can use with the |EX-CS|. These options are simple and inexpensive (i.e. free) and are suitable for initial testing if you have installed *just* the recommended hardware (including WiFi). Namely **WiFi** (using a smart phone) and **Direct Connection**.

For further throttle and connection options, refer to :doc:`/ex-commandstation/advanced-setup/controllers`.

----

Connecting via WiFi
-------------------

For those who just want to run trains and not use any other control software, the simplest method to get going is to download a compatible phone or tablet app and connect directly from your wireless device to the |EX-CS|. 

Note you need a Command Station with a WiFi Shield. 

Here is an image that represents a direct connection.

.. figure:: /_static/images/throttles/throttle_wifi_direct.png
   :alt:  WiFi Throttle Direct to CS
   :align: center
   :scale: 40%

   WiFi Throttle Direct to Command Station

There are number of excellent :doc:`phone apps and physical hardware devices </throttles/index>` that can be used as a WiFi Throttle (Controller) for the |EX-CS|.  On this page we are only going to cover two. 

.. warning:: 
   
   This warning is only relevant to the **DIY** EX-CommandStation. |BR|
   **It is not relevant to the** |EX-CSB1-SHORT|. 

   Be aware that the Espressif firmware shipped with *Duinopeak ESP8266 WiFi Expansion* and *ESP-01 or ESP-01S* devices :dcc-ex-red-bold:`probably will NOT work` with |EX-CS| out of the box.

   The recommended :doc:`Makerfabs ESP8266 WiFi Shield </reference/hardware/wifi-boards/makerfabs-esp8266>` is now shipping with the correct firmware version and **will work** with |EX-CS| *without modification*.

   If you see a WiFi network Name (SSID) of ``DCCEX-SAYS-BROKEN-FIRMWARE`` then you have one of the problematic AT firmware versions.  This can be corrected, but is probably beyond Conductor level and requires additional hardware.  |BR| 
   See :doc:`/support/wifi-at-version` for details on how to check the version and how to correct it if needed.

|hr-dashed|

Compatible WiFi Throttles
^^^^^^^^^^^^^^^^^^^^^^^^^

.. important:: 
   :class: important-float-right
   
   A limitation of |Access Point Mode|, which is recommended in the :doc:`/ex-commandstation/index` pages, is that the |WiThrottle Server| of the |EX-CS| cannot be 'discovered'.  |Engine Driver| can *usually* guess it, but |WiThrottle| can't.  In |WiThrottle| you will need to type in the address.

For more information on any of these throttles, you can click on their links below or see our :doc:`Throttles Page Index </throttles/index>`.

We will cover the use of just two here. These two are a) free, or have a free version, b) are reasonably easy to get to work, and c) most people will already have a suitable phone to use:

If you have an Android phone use :doc:`/throttles/software/engine-driver`. |br| If you have an Apple (iOS) phone use :doc:`/throttles/software/withrottle`.

|hr-dashed|

Engine Driver (Android \| WiThrottle \| WiFi)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

|Engine Driver| is a throttle app for your phone that can control multiple locos and your turnouts/points. It uses an interface called "|WiThrottle Protocol|" (for WiFi Throttle). Any |WiThrottle Protocol| compatible throttle will work with the |EX-CS|. There are two ways to connect Engine Driver to your |EX-CS|:

* The first method is to connect directly to the Command Station via WiFi. You will need either a |EX-CSB1| with its integrated WiFI, or a WiFi board connected to your DIY Command Station (see WiFi Setup :doc:`WiFi Setup </ex-commandstation/diy/wifi-setup>`).
* The second method is to use |JMRI| and connect |Engine Driver| (ED) to the computer running |JMRI|. (We won't cover that option here.)

Basic use of |Engine Driver| will be covered on the following :doc:`/ex-commandstation/testing-diy` page. (See :doc:`Engine Driver Page </throttles/software/engine-driver>` for additional details on how to install and run |Engine Driver|.)

|hr-dashed|

WiThrottle Lite (iOS \| WiThrottle \| WiFi)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

|WiThrottle| is an app for iPhones and iPads. It can connect directly to the |EX-CS| like |Engine Driver| does, or connect to |JMRI| on a computer and then have |JMRI| connect to the Command Station via a USB cable.

The "Lite" version of |WiThrottle| is free and is more than adequate for some initial testing and base running of locos. However the Lite version does not have a Track Power button/command so it is important to configure your |EX-CS| to power on at startup.

Basic use of |WiThrottle| will be covered on the following :doc:`/ex-commandstation/testing-diy` page.  (See :doc:`WiThrottle Page </throttles/software/withrottle>` for details on how to install and run |WiThrottle|.)

----

Connecting via USB
------------------

Here are the connections, just a computer running a chromium-based browser (Chrome, Edge, Safari and others) a USB cable, and your |EX-CS|.

.. figure:: /_static/images/throttles/webthrottle_setup.png
   :alt: EX-WebThrottle
   :align: center
   :scale: 40%

   EX-WebThrottle

|hr-dashed|

Compatible USB Throttles
^^^^^^^^^^^^^^^^^^^^^^^^^

There is currently only one USB compatible Throttle (Controller) for the |EX-CS| that we are aware of.

|hr-dashed|

Our EX-WebThrottle (DCC-EX Native Commands | USB/Serial)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The simplest throttle option is to just use a throttle directly connected to the Command Station. The simplest of these is arguably |EX-WT|, connected via a USB cable from your computer and web browser directly to the Command Station. You have control of multiple locomotives and can operate turnouts/points. There is a way to replace the USB cable with a wireless connection, but we will cover that later in the Wireless USB Bridge section. Below is a picture of |EX-WT| with the side menu open. You can click on the image to see it full size.

.. figure:: /_static/images/throttles/webthrottle1.jpg
   :alt: EX-WebThrottle
   :align: center
   :scale: 40%

   EX-WebThrottle

|hr-dashed|

Basic use of |EX-WT| will be covered on the following :doc:`/ex-commandstation/testing-diy` page.  (For additional operating instructions see :doc:`how to use EX-WebThrottle </ex-webthrottle/index>`)

|HR-HEAVY|

Next Steps - Testing your setup 
===============================

Click the 'Next' button below to learn how to test your |EX-CS|.
