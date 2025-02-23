.. include:: /include/include.rst
.. include:: /include/include-l3.rst
.. include:: /include/include-hardware.rst
|EX-CS-LOGO|

************************************
Velleman KA03 (kit) VMA03 (soldered)
************************************

|SUITABLE| |engineer| |support-button|

.. warning:: 

   This board is **not** compatible with |TM| DC mode.

**THIS BOARD HAS NO CURRENT SENSE!** Refer to the :ref:`reference/hardware/motorboards/motor-board-config:current sense and sense factor` section for further information.

Must cut traces and solder resistors to get current sensing on the soldered board. Much easier to simply not solder the pins on the kit version. Pin assignments must be added to a new motorboard entry in the config.h file.

.. image:: /_static/images/motorboards/velleman_motor.jpg
   :alt: Velleman KA03
   :scale: 100%
