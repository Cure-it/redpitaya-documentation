*****
Wired
*****

.. _LAN:

========================
Local Area Network (LAN)
========================

This is the most common and recommended way of connecting and using your Red Pitaya boards.
Your LAN network needs to have DHCP settings enabled, which is the case in the majority of the local networks. With this, a simple *plug and play* approach is enabled.
Having the Red Pitaya board connected to the local network will enable quick access to all Red Pitaya applications using only your web browser.
Simply follow this 3 simple steps:

1. Connect the power supply to the Red Pitaya board,
2. Connect the Red Pitaya board to the router or direc to the PC Ethernet socket,
3. Open your web browser and type: ``rp-xxxxxx.local/`` into the URL field.
       
.. note::

   ``xxxxxx`` are the last 6 characters from MAC address of your Red Pitaya board.
   The MAC address is written on the Ethernet connector.
    
.. figure:: connect-2.png
    
   Figure 1: Connecting your Red Pitaya board to the LAN network.

After the **third step** you will get a Red Pitaya main page as shown below.

.. figure:: connect-3.png

   Figure 2: Red Pitaya main page user interface.

.. _dir_cab_connect:

================================
Direct Ethernet cable connection
================================

If the user is restricted from having Red Pitaya boards on the DHCP LAN network **permanently**, there is a way to connect directly to your Red Pitaya board. 

**Direct Ethernet Connection** was enabled from the start, but until now some additional settings on the user's PC (**static IP configuration**) were required to properly configure the connection.
This step has been eliminated with the NEW OS 0.97 (and newer) and the only step needed is to plug the ethernet cable from your PC to the Red Pitaya board. 

.. figure:: connect-10.png

**Here is the procedure for a direct Ethernet connection:**


**Windows 7,8,10** (the Bonjour service must be installed for Win 7/8)

1. Connect the Ethernet cable and wait 30 sec
2. Open the web browser and type **rp-xxxxxx.local/** in the URL field
   

**Linux / Ubuntu**

1. Open Network settings, Edit Connection, and for the LAN network, select Method **Share to other computers** under IPv4 Settings.
2. Connect the Ethernet cable and wait 30 sec
3. Open the web browser and type **rp-xxxxxx.local/** in the URL field
   
    
**MAC**

1. Connect the Ethernet cable and wait 30 sec
2. Open the web browser and type **rp-xxxxxx.local/** in the URL field
   

.. note::

      ``xxxxxx`` are the last 6 chracters from the MAC address (on the Ethernet connector)

.. warning::

      If you experience some problems when using the Direct Ethernet Connection described above, try to **disable the WiFi** connection on **your PC** (if it has been enabled) and **reset the Red Pitaya** board (power off/on). If the problem still persists, you can try the STATIC IP configuration described below.

-----------------------
Static IP configuration
-----------------------

This type of connection requires additional settings on your PC and Red Pitaya board. 

.. note::

   This connection is also arranged via the Network Manager application, so users should first have access to the LAN (DHCP) network in order to arrange a static IP on the Red Pitaya board. 
    
How to set up a direct Ethernet connection is described below.

The first step is connecting the Red Pitaya board directly to the LAN network and setting a static IP on it. 

1. Use the recommended connection described in **Local Area Network (LAN)** section.
   Once you are successfully connected to your Red Pitaya board, open Network Manager and choose the ``Static`` option.
   Input the static IP and click **Apply**.

   .. figure:: connect-11.png

2. The second step is to set a network setting on the PC.
   Here is an example on Ubuntu 14.04, but it is very similar on other operating systems as well.
   To set up a direct connection with your PC, follow these next steps:
    
   1. Launch Network Manager on your computer. 
   2. Add a new Ethernet connection.
      **(There is no need to create a new network since you can set static IP settings on the existing network and skip all steps up to step 5.)**

   .. figure:: connect-12.png

3. Select **Ethernet** connection and press **Create** button.

   .. figure:: connect-13.png

4. Select the name of the new Ethernet connection.

   .. figure:: connect-14.png

5. Select **Method – Manual**, press the **Add** button, and insert:

   - The static IP address of your PC (must be different from the IP address of the Red Pitaya board), 
   - Netmask (input: 255.255.255.0)
   - Gateway (can be left empty)
   - DNS servers (can be left empty) and click the **Save** button.

   .. figure:: connect-15.png 

.. note::

    Once you have these settings arranged, connect the Ethernet cable between your Red Pitaya board and PC, open a web browser, in the web browser URL field, input the chosen Red Pitaya board static IP (in our example, ``192.168.0.15``) and press enter.

.. figure:: connect-16.png 

********
Wireless
********
    
===========================
Wireless Network Connection
===========================

This type of connection will enable wireless connection to the Red Pitaya board via your local WiFi network.
In order to connect your Red Pitaya board to the same WiFi network to which you have connected your PC/Laptop, you first need to use a LAN connection.
Access your Red Pitaya board via a web browser and start the Network Manager application.
Through this application, all network settings of the Red Pitaya board are manageable.
Simply select the desired WiFi network, input the password, and select connect.
Once you have arranged a WiFi network, you don't need a LAN connection anymore, and after the restart of the Red Pitaya board, it will connect to the preset WiFi network automatically.

.. note::

   A WiFi dongle is required to connect the Red Pitaya to a WiFi network (|RP store Dongle|). Please note that not all are |compatible|.

.. |RP store Dongle| raw:: html

    <a href="https://redpitaya.com/product/red-pitaya-wi-fi-dongle/" target="_blank">Red Pitaya WiFi dongle</a>

.. |compatible| raw:: html

    <a href="https://redpitaya.readthedocs.io/en/latest/developerGuide/software/other_info/os/network.html#supported-usb-wifi-adapters" target="_blank">compatible</a>


.. figure:: connect-4.png

Steps on how to connect your Red Pitaya board over a WiFi network are described below:
 
#. Start your Red Pitaya web user interface (Use the connection described in |LAN connection|)

.. |LAN connection| raw:: html

    <a href="https://redpitaya.readthedocs.io/en/latest/quickStart/connect/connect.html#local-area-network-lan" target="_blank">Local Area Network (LAN) connection</a>

#. Open Network Manager application
#. Insert the WiFi dongle into the USB plug on the Red Pitaya board.
   The recommended WIFI USB dongle is the Edimax EW7811Un.
   In general, all WIFI USB dongles that use the RTL8188CUS chipset should work.
    
    .. figure:: connect-5.png

#. When the USB WiFi dongle is plugged in, the system will recognise it and enable additional settings.
#. Select Client Mode, the desired WiFi network, enter your password and press the Connect button.

   .. figure:: connect-6.png

#. When your Red Pitaya board is connected, the IP address will be shown on the user interface. This IP address is only for the WiFi connection.
   You can check the connection by inputting a WiFi IP address in the web browser URL field (press enter after inputting). 
   
   .. figure:: connect-7.png   

Now you have a WiFi connection established.
If you restart the Red Pitaya board, it will connect to the selected network automatically (if the selected network is available).
Also, you can disconnect the LAN connection and your board will still be available over the WiFi network, i.e., over the WiFi IP address.
    
.. note::
    
   WiFi networks are generally not robust, and the full performance of the Red Pitaya application can be affected.  
   
.. note::

    When using the Raspberry Pi WiFi dongle, an issue of the dongle not being detected can arise. To mitigate this, detach the power cable from the Red Pitaya and wait for about a minute before powering up the Red Pitaya again.
        
=================
Access Point Mode
=================

When there are no LAN or WiFi networks available, Red Pitaya can act as an access point.
This will allow you to connect your PC, laptop, tablet, or smart phone directly to the Red Pitaya over WiFi.

.. note::

   To use Red Pitaya as an access point, a |Raspberry Pi USB WiFi| dongle is needed.
   
.. |Raspberry Pi USB WiFi| raw:: html

    <a href="https://www.raspberrypi.org/products/raspberry-pi-usb-wifi-dongle/" target="_blank">Raspberry Pi USB WiFi</a>

.. figure:: connect-8.png

Follow the steps below to enable the access point and connect to it.

1. Start your Red Pitaya web user interface (Use the connection described in |LAN connection|)
2. Open Network Manager application
3. Input the name and password of the access point network to be created. The password name should be at least 8 characters long. Do not use special signs.
4. Connect your PC, laptop, tablet, or phone to the network created by the Red Pitaya board.
5. Input the Access Point network IP address into the web browser URL field and press enter.
    
.. note::

   When Access Point is enabled on Red Pitaya, it will continue to boot in Access Point configuration until it is disabled in the Network Manager.
   
.. note::
    
   The IP address in Access Point mode is always the same: ``192.168.128.1``

.. figure:: connect-9.png
