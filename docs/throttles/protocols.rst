.. include:: /include/include.rst
.. include:: /include/include-l1.rst
.. include:: /include/include-throttles.rst
|EX-THROTTLES-LOGO|

***************************************************************
WiThrottle Server, Web Server, DCC-EX Native Protocol Explained
***************************************************************

|SUITABLE| |conductor| |tinkerer| |engineer| |support-button| 

.. sidebar:: 
   :class: sidebar-on-this-page

   .. contents:: On this page
      :depth: 2
      :local:

There are several competing standards and ways to connect external software such as Throttles (Controllers) to the |EX-CS| directly or indirectly through |JMRI|. These standards are called "protocols" and the definition and instructions for how to implement them is called an API (Application Programming Interface). There is the |WiThrottle Protocol| API using a |WiThrottle Server|, the JMRI API using a Web Server, and the DCC-EX API using |DCC-EX Native Commands|. You need to know that the language your throttle uses will work with how you want to connect to your Command Station.

The DCC-EX Native Protocol
==========================

The first way to connect to |EX-CS| is to use our |DCC-EX Native Protocol|. This is the set of commands that tell the Command Station how to control your trains. |EX-CS| understands simple command surrounded by brackets like this: "<1 MAIN>". That command turns your main track power on.

Since this is just sending characters back and forth across a serial connection, anything that can connect to an Arduino through a USB cable or one of the other serial ports using WiFi of Bluetooth can send |DCC-EX Native Commands| to the Command Station. This method is fast, direct, and can take advantage of special features that exist only in |EX-CS|. You can even connect using the |IDE Serial Monitor| or connect to our WiFi with a terminal program like PuTTY and type |DCC-EX Native Commands| manually. Our |EX-WT|, |JMRI| and throttles (controllers) like |Engine Driver|, *DCCpp CAB* and *DigiTrainsPro* send commands in DCC-EX Native format.  

Refer to :ref:`this list <throttles/index:dcc-ex (dcc-ex native commands)>` for the Throttles (Controllers) that are known to support the DCC-EX Native Protocol.

The WiThrottle Server
=====================

The |WiThrottle Protocol| is the proprietary protocol developed by Brett Hoffman at https://www.WiThrottle.com |EXTERNAL-LINK|. Like the |DCC-EX Native Protocol|, is consists of messages composed of strings of text characters sent across a serial connection that tell the Command Station how to control your layout. The command "PPA1", for example turns the power on in WiThrottle. It can be confusing, but WiThrottle can refer to the protocol (as in |WiThrottle Server| or WiThrottle compatible), but it also refers to the iOS throttle App called "WiThrottle" (it stands for WiFi Throttle).

|EX-CS| allows you to use the "|WiThrottle server|" built into |JMRI| and other software and have them connect to your Command Station via a USB or serial connection, but |EX-CS| also implements a |WiThrottle Protocol| server in our Command Station software itself. A "server" is just a fancy way of saying that there is software running inside |JMRI| and |EX-CS| that can understand WiThrottle commands and "serve" or "service" clients that want to connect and send WiThrottle commands. The ability of |EX-CS| to natively "speak" WiThrottle means you can directly connect a |WiThrottle protocol| compatible Throttle (aka CAB) via WiFi or Bluetooth to the Command Station and run trains. But you can still connect to JMRI WiThrottle instead and connect |JMRI| to |EX-CS| with a USB cable. So |EX-CS| is bi-lingual, we speak DCC-EX AND |WiThrottle Protocol|! Apps like |Engine Driver| and |WiThrottle| for iOS send commands in the WiThrottle format.

Refer to :ref:`this list <throttles/index:wiThrottle Protocol Based Throttles>` for the Throttles (Controllers) that are known to support the |WITHROTTLE PROTOCOL|.

The JMRI WEB Server
====================

|JMRI| has two kinds of servers you can connect to built into the |JMRI| software. We already mentioned the |WiThrottle server|, but |JMRI| also has a WEB Server. Devices can connect to |JMRI| and send commands like it would to a WEB page. This is yet another protocol and is supported by throttles like DigiTrainsPro. When connecting using a throttle that uses the WEB Server, you connect your throttle to that via WiFi, and then connect to |EX-CS| with a USB or Serial connection.

Refer to :ref:`this list <throttles/index:JMRI Web Server Based Throttles>` for the Throttles (Controllers) that are known to support the JMRI Web Server Protocol.

A Note about WiFi Dropped Connections
=======================================

Phones and laptop like to think they are "smart" and want to connect you to the strongest signal and to a network that has internet capability. If you use the |EX-CS| as an Access Point (AP), which doesn't connect to the internet, and you connect to |EX-CS| with your throttle, your device may disconnect you from the Command Station without you knowing and without your permission. You should turn off the option to "automatically connect" to your home network. You may even have to "forget" your home network when you are using your wireless device to connect to |EX-CS|. If you would rather, you can change settings in your config.h file to connect to your home network as a client instead running as an AP, and then have your throttle devices find the Command Station by its IP Address on your home network. You can find out more about that in :doc:`Wifi Setup </ex-commandstation/diy/wifi-setup>`

