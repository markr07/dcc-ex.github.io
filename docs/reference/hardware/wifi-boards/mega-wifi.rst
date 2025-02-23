.. include:: /include/include.rst
.. include:: /include/include-l3.rst
.. include:: /include/include-hardware.rst
|EX-CS-LOGO|

*********************
Mega+WiFi Combo Board
*********************

|SUITABLE| |conductor| |tinkerer| |engineer| |support-button| 
   
.. warning:: 
   :class: warning-float-right

   Buyer beware! There have been numerous reports of build quality issues with these clone boards, with poorly soldered USB connectors and issues getting wireless working two commonly reported issues.

   The DCC-EX team do not recommend the combined Mega2560 + WiFi due to the number of issues encountered in recent times.

.. figure:: /_static/images/assembly/mega_wifi.png
   :alt: Mega + WiFi Combo Board
   :scale: 35%

   Mega + WiFi Combo Board

The Mega+WiFi is a board from China that combines an Arduino Mega design with an on-board ESP8266 WiFi chip.

The advantage of this configuration is that with WiFI on the same board with the Microcontroller, you only need two boards. Your "stack" will have just the Mega+WiFi board with the |motor shield| on top. 

The disadvantage is that you will have to "flash" (upload new firmware) to the ESP chip on the board. This requires a computer, downloading a flash tool and a zipped data file, setting some switches, connecting the Mega+WiFi to the computer with a USB cable, and uploading the new firmware. 

A |Conductor-text| should be able to follow the instructions, but Tinkerers may feel more comfortable. It takes about 15-20 minutes from start to finish (read, download, unzip, flash, done). 

:doc:`Click on this link</reference/hardware/microcontrollers/wifi-mega>` for detailed instructions on exactly how to configure and use a Mega+WiFi board.
