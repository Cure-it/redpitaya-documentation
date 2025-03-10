##############
Logic Analyzer
##############

.. figure:: Slika_01_LA.jpg

The Logic Analyzer application enables the representation of the binary states of digital signals. The Logic Analyzer can both deal with purely binary signals, such as GPIO outputs of the Raspberry Pi or Arduino board, as well as analyse different buses (I2C, SPI, and UART) and decode the transmitted data. All Red Pitaya applications are web-based and do not require the installation of any native software. Users can access them via a web browser using their smartphone, tablet, or a PC running any popular operating system (MAC, Linux, Windows, Android, and iOS).

.. note::

    An additional extension module is needed to use the *Logic Analyzer PRO* application. The module can be purchased from the |RP_store|.

.. |RP_store| raw:: html

   <a href="https://redpitaya.com/shop/" target="_blank">Red Pitaya store</a>

The graphical user interface of the Logic Analyzer fits well into the overall design of the Red Pitaya applications, providing the same operating concept. The Logic Analyzer user interface is shown below.

.. figure:: Slika_02_LA.png

Apart from the actual graph, there are five key areas/elements into which the surface is divided:

   1. **Auto:** Resets the zoom and brings the trigger event to the middle of the graph.
   #. **Run / Stop:** Starts recording the input signals and interrupts them while recording is active.
   #. **Channels / trigger / Measuring Tools:** This menu provides controls for inputs, triggers, and guides.
   #. **Axis control panel:** The horizontal +/- buttons enable you to select the scaling of the X axis and to change it, and to select the time range displayed in the graph. The vertical +/- buttons change the Y axis, and thus the height of the graph display. In addition, the settings for the time frame, trigger, and sampling rate are displayed.
   #. **Status Display:** Displays information about the current state of the recording (stop, wait, ready).

Features
********

ANALYZING BINARY SIGNALS
========================

.. figure:: Slika_03_LA.png

By selecting the gear button behind the "DIGITAL" selection field, you enter the menu for the channel configuration. In the LINES register, the channels can be activated or deactivated by simply clicking the check mark. As long as no bus systems have been configured, the channels operate as purely digital inputs and correspondingly show the progress. The ACQ tab opens the selection field for the sample rate settings. When selecting the values, there is one thing to note: the sample rate has a significant influence on the time section, which can be represented. The memory depth of the Logic Analyzer application is 1 MS, so it can store and display 1,000,000 binary values. From this, it is clear that the sampling rate determines how many values are recorded per second. If we chose the highest sampling rate (125 MS/s), 125,000,000 values would be recorded per second. Since 1,000,000 values can be stored in the time memory, we get a 0.008 second time window. With a sampling rate of 1 MS/s, the time window of the recorded signal will be one full second.

.. figure:: Slika_04_LA.png

When the pre-sample data buffer value is set, the trigger event of the recording is located. This makes particular sense if you want to find out what happened before the defined trigger event. To illustrate with an example, the sample rate is set to 4 MS/s. The stored time segment thus amounts to approximately 0.25 s = 250 ms. If the pre-sample data buffer is set to 10 ms, then the recorded signal shows what has happened 10 ms before the event and 240 ms after the event.

TRIGGER:
========

.. figure:: Slika_05_LA.png

By clicking the gear behind TRIG settings, the trigger menu is opened. Each channel can be set as a trigger source with the desired condition. For acquisition to start, the trigger source and rising edge need to be defined.

The possible criteria for a trigger event are the following:

     - **X - Ignore:** no event
     - **R - Rising:** Risinge edge
     - **F - Falling:** Falling edge
     - **E - Either:** Edge change (rising or falling edge)

By clicking the RUN button, the recording is started. The status display informs you whether the process is still running (WAITING) or has already been completed (DONE). After finishing the acquisition, the results are displayed in a graph. Additional trigger options, LOW and HIGH, are used for the so-called pattern triggering. For example, if you set the trigger source to be DIN0 – Rising edge (to have one channel defined as a trigger source with a rising or falling edge is a mandatory condition for the acquisition to start), DIN1 to HIGH and DIN2 to LOW, this will cause such a behaviour that the application logic will wait for the state where DIN0 goes from 0 to 1, DIN1 is 1, and DIN2 is 0 to start the acquisition.

DECODE BUS DATA:
================

In the DIGITAL → BUS menu, the decoding of the desired lines can be selected. Up to four buses can be defined. The available decoding protocols are I2C, UART, and SPI. By selecting the desired protocol, the settings menu for the selected protocol is opened.

.. figure:: Slika_06_LA.png

For the display of the decoded data, two options are possible: firstly, the data is placed as a separate layer in the graph directly on the signal. Secondly, using the DIGITAL → DATA menu, where the decoded data is represented in a table format. You can select ASCII, DEC, BIN, and HEX data formatting. With the EXPORT button, the decoded data can be packed into a CSV file. This then ends up directly in the download folder and can be used for further analysis.

.. figure:: Slika_07_LA.png

CURSORS:
========

As with the Oscilloscope the Logic Analyzer App also provides CURSORS for quick measurements. Because there are no variable amplitude readings but only discrete signal levels, the cursors are available exclusively for the X axis.
When enabled, the cursors will show the relative time to zero point (trigger event) and the difference between the two.

.. figure:: Slika_08_LA.png

Specifications
**************

+-------------------------+----------------------+----------------------+
|                         | Direct E1 connection | LA extension module  |
+-------------------------+----------------------+----------------------+
| Channels                | 8th                  | 8th                  |
+-------------------------+----------------------+----------------------+
| Sampling rate (max.)    | 125 MS/s             | 125 MS/s             |
+-------------------------+----------------------+----------------------+
| Maximum Input Frequency | 50 MHz               | 50 MHz               |
+-------------------------+----------------------+----------------------+
| Supported bus protocols | I2C, SPI, UART, CAN  | I2C, SPI, UART, CAN  |
+-------------------------+----------------------+----------------------+
| Input voltage           | 3.3 V                | 2.5 ... 5.5 V        |
+-------------------------+----------------------+----------------------+
| Overload protection     | not available        | integrated           |
+-------------------------+----------------------+----------------------+
| Level thresholds        | | 0.8V (low)         | | 0.8V (low)         |
|                         | | 2.0V (high)        | | 2.0V (high)        |
+-------------------------+----------------------+----------------------+
| Input impedance         | 100k, 3 pF           | 100k, 3 pF           |
+-------------------------+----------------------+----------------------+
| Trigger types           | Level, edge, pattern | Level, edge, pattern |
+-------------------------+----------------------+----------------------+
| Memory depth            | 1 MS (typical)       | 1 MS (typical)       |
+-------------------------+----------------------+----------------------+
| Sampling interval       | 8 ns                 | 8 ns                 |
+-------------------------+----------------------+----------------------+
| Minimum pulse duration  | 10 ns                | 10 ns                |
+-------------------------+----------------------+----------------------+


Hardware/Connections
====================

The Logic analyzer extension module is recommended for maximum performance of the Logic Analyzer application and protection of your Red Pitaya board. Using the LA extension module is straightforward; just plug it into your Red Pitaya and connect the leads to the desired measurement points.

.. figure:: Slika_09_LA.png

To use the Logic Analyzer without the extension module, you need to be more careful in connecting the logic analyzer probes to the |E1| on the Red Pitaya board. The pins used for the logic analyzer board are shown in the picture below.


.. |E1| raw:: html

   <a href="https://redpitaya.readthedocs.io/en/latest/developerGuide/hardware/125-14/extent.html#extension-connector-e1/" target="_blank">extension connector E1</a>

.. note::

    Direct use of the GPIO |E1| pins of the Red Pitaya board works only with STEMlab 125-10! The connection for the STEMlab 125-10 board is shown in the image below (left).
    
.. figure:: Slika_10_LA.png
