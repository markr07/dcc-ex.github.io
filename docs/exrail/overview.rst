.. include:: /include/include.rst
.. include:: /include/include-l1.rst
.. include:: /include/include-ex-r.rst
|EX-R-LOGO|

********
Overview
********

|SUITABLE| |conductor| |tinkerer| |engineer| |support-button| 

.. sidebar:: 
   :class: sidebar-on-this-page

   .. contents:: On this page
      :depth: 2
      :local:

Welcome to the home for |DCC-EX| Automation.

|EX-R| is an "|EX-R-FULL|"
that can easily be used to describe sequential command 'sequences' to automatically take place on your model layout. These sequences are defined programmatically in a simple command script file, and uploaded to the Command Station once to configure it. |EX-R| will then run automatically on **EX-CommandStation** startup, trigger manually, or on occurrence of the specified events.

To begin, let's define a few terms:

**OBJECT** - Things / devices on your layout that you want to interact with. these include: :ref:`Your locos <exrail/creating-elements:adding a roster>`, :ref:`Turnouts/Points <exrail/creating-elements:adding the hardware - servo turnouts/points>`, :ref:`semaphores/Signals <exrail/creating-elements:adding the hardware - signals>`, :ref:`Servo based Animations <exrail/creating-elements:configure myautomation.h - servos for signals an animations>`, :ref:`Sensors <exrail/creating-elements:adding the hardware - sensors>` and :ref:`Signals (Lights) <exrail/creating-elements:configure myautomation.h - signals>`.

**SEQUENCE** - Simply a list of things to be done in order. These things might be to actually drive a train around, or merely to set some turnouts or flash some scene or panel lights. Actions can be made to wait for conditions to be met, like a sensor detecting a train, a button being pushed, or a period of time elapsing.

**ROUTE** - A special type of SEQUENCE that is made visible to a throttle with a readable name so the user can press a button to get the sequence executed. This might be best used to set a series of turnouts and signals to create a route through the layout.

**AUTOMATION** - A special type of SEQUENCE that is made visible to a throttle so that a user can hand over a loco and let |EX-R| drive the train away, following each step listed in the sequence.

Most people wanting to do animations or run trains through an automated route will use a SEQUENCE, but those with :doc:`throttles </throttles/index>` that support it (|engine driver|, |EX-WT|) can add routes and automations. Both of these terms are just tags that let throttles with this feature automatically assign sequences to control buttons. "Routes" go into route buttons and can set turnouts, signals, etc., so you can drive your train along that route. Automation 'sequences' can appear on a 'handoff' button that will supply or handoff the Loco ID to |EX-R| where it can take over and run the train autonomously. An automation sequence example would be manually driving a train into a station and pressing the assigned handoff button in the throttle that runs an AUTOMATION to take it on a journey around the layout.

Things You Can Do With EXRAIL
==============================

- Create 'Routes' which set multiple turnouts/points and signals at the press of a button in |EX-WT| or |Engine Driver|, |WiThrottle|, or other WiThrottle-compatible throttles are available
- Automatically drive multiple trains simultaneously, and manage complex interactions such as single line working and crossovers by setting up Automations 'Sequences'
- Drive trains manually, and hand a train over to an Automation
- Animate accessories such as lights, crossings, or cranes
- Intercept turnout/point changes to automatically adjust signals or other turnouts
- Turn on the coffee pot when the train reaches the station

.. rst-class:: clearer

What You Don't Need
===================

While extra functionality may be attained by using additional tools and applications, to get the benefit of |EX-R| you don't need anything more than a |EX-CS|, *and the Arduino IDE* used to configure it.

You DON'T need:

- |JMRI|, or any additional utilities
- |Engine Driver|, |WiThrottle|, or any other WiThrottle app
- A separate computer living under your layout
- Knowledge of C++ or Python/Jython programming

Reasons to use EXRAIL rather than extra software and/or hardware
=================================================================

I have used C++ on Arduino's and Python/Jython on |JMRI| software to build Automation sequences. I now use |EX-R| instead because:

- It's significantly easier and more flexible than the other two options.
- I reduce the number of Uno and Nano accessory boards needed to do the same tasks on the layout by using the |DCC-EX| Command Station and embedded |EX-R| instead.
- I can create Automations, Routes, & Sequence scripts With |EX-R| on the Command Station and still access them from |JMRI| PanelPro and DecoderPro GUI buttons with a simple sendDCCmessage.py script pointer that passes them to the |EX-R| scripts on the Command Station, so I don't have to rewrite the script in Jython/Python.
- |EX-R| is ten times easier to learn and use and is more flexible then the other methods.

|HR-HEAVY|

Next Steps - myAutomation.h
===========================
   
See the :doc:`editing` page or click the 'Next' button to learn how to edit the file which will contain your automation sequences.