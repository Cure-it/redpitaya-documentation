Generate a signal on external trigger
#####################################

.. http://blog.redpitaya.com/examples-new/generate-signal-on-fast-analog-outputs-with-external-triggering/

Description
***********

This example shows how to program Red Pitaya to generate an analog signal on an external trigger. Red Pitaya will first wait for a trigger from an external source and start generating the desired signal right after the trigger condition is met. Voltage and frequency ranges depend on the Red Pitaya model.


Required hardware
*****************

    - Red Pitaya device

.. figure:: output_y49qDi.gif

Code - MATLAB®
**************

The code is written in MATLAB. In the code, we use SCPI commands and TCP client communication. Copy the code from below into the MATLAB editor, save the project, and hit the "Run" button.

.. code-block:: matlab

    %% Define Red Pitaya as TCP client object
    clc
    clear all
    close all

    IP = '192.168.178.56';          % Input IP of your Red Pitaya...
    port = 5000;
    RP = tcpclient(IP, port);

    %% Open connection with your Red Pitaya
    RP.ByteOrder = "big-endian";
    configureTerminator(RP,"CR/LF");

    flush(RP);                      % clear input & output buffers
    % flush(RP, 'input')
    % flush(RP, 'output')

    %% Generate

    writeline(RP, 'GEN:RST')

    writeline(RP,'SOUR1:FUNC SINE');            % Set function of output signal {sine, square, triangle, sawu, sawd, pwm}
    writeline(RP,'SOUR1:FREQ:FIX 200');         % Set frequency of output signal
    writeline(RP,'SOUR1:VOLT 1');               % Set amplitude of output signal

    writeline(RP,'SOUR1:BURS:STAT CONTINUOUS'); % Set burst mode to CONTINUOUS
    writeline(RP,'SOUR1:BURS:NCYC 1');          % Set 1 pulses of sine wave
    writeline(RP,'SOUR1:TRIG:SOUR EXT_PE');     % Set generator trigger to external

    writeline(RP,'OUTPUT1:STATE ON');           % Set output to ON
    writeline(RP,'SOUR1:TRIG:INT');

    % For generating signal pulses, your trigger signal frequency must be less than
    % frequency of generating signal pulses. If your trigger signal frequency
    % is higher than the frequency of generating signal pulses
    % you will get a continuous signal on output, instead of pulses.


    clear RP;


Code - C
********

.. note::

    Although the C code examples don't require the use of the SCPI server, we have included them here to demonstrate how the same functionality can be achieved with different programming languages. 
    Instructions on how to compile the code are |compiling and running C|.
    
.. |compiling and running C| raw:: html

    <a href="https://redpitaya.readthedocs.io/en/latest/developerGuide/software/build/comC.html#compiling-and-running-c-applications" target="_blank">here</a>

.. code-block:: c

    /* Red Pitaya external trigger pulse generation Example */

    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>

    #include "rp.h"


    int main(int argc, char **argv){

        /* Print error, if rp_Init() function failed */
        if(rp_Init() != RP_OK){
            fprintf(stderr, "Rp api init failed!\n");
        }

        rp_GenReset();

        rp_GenWaveform(RP_CH_1, RP_WAVEFORM_SINE);
        rp_GenFreq(RP_CH_1, 200);
        rp_GenAmp(RP_CH_1, 1);

        rp_GenBurstCount(RP_CH_1, 1);
        rp_GenMode(RP_CH_1, RP_GEN_MODE_BURST);
        rp_GenTriggerSource(RP_CH_1, RP_GEN_TRIG_SRC_EXT_PE);

        rp_GenOutEnable(RP_CH_1);
        rp_GenTriggerOnly(RP_CH_1);

        /* Release rp resources */
        rp_Release();

        return 0;
    }


Code - Python
*************

.. code-block:: python

    import sys
    import redpitaya_scpi as scpi

    rp_s = scpi.scpi(sys.argv[1])

    wave_form = 'sine'
    freq = 10000
    ampl = 1

    rp_s.tx_txt('GEN:RST')

    rp_s.tx_txt('SOUR1:FUNC ' + str(wave_form).upper())
    rp_s.tx_txt('SOUR1:FREQ:FIX ' + str(freq))
    rp_s.tx_txt('SOUR1:VOLT ' + str(ampl))
    rp_s.tx_txt('SOUR1:BURS:NCYC 2')
    rp_s.tx_txt('SOUR1:BURS:STAT BURST')
    rp_s.tx_txt('SOUR1:TRIG:SOUR EXT_PE')

    rp_s.tx_txt('OUTPUT1:STATE ON')
    rp_s.tx_txt('SOUR1:TRIG:INT')


Code - LabVIEW
**************

.. figure:: Generate-signal-on-external-trigger_LV.png

`Download <https://downloads.redpitaya.com/downloads/Clients/labview/Generate%20signal%20on%20external%20trigger.vi>`_
