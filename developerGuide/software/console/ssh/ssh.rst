.. _ssh:

###############################
Establish remote SSH connection
###############################

Access information for SSH connection:

* Username: ``root``
* Password: ``root``

If you are unable to connect, check that Red Pitaya is connected to your :ref:`local network <isConnected>`.
    
Connection instructions are available for:

.. contents::
    :local:
    :backlinks: none
    :depth: 1
    
==========
Windows 10
==========

For this example, `PuTTy tool <http://www.putty.org/>`_
was used on Windows XP and Windows 7 Starter OS.
Run PuTTy and enter the Red Pitaya's IP address into
**Host Name (or IP address)** field.

.. figure:: 445px-PuTTy_connection_settings.png
   :align: center

   PuTTy SSH connection settings.
    
If you attempt to connect to Red Pitaya for the first time,
a security alert will pop-up asking you to confirm the connection.
At this time, the ssh-key will be added to the registry in your computer.
Command prompt pops-up after login is successful.

When connected to RP via SSH (PuTTy) you get the following command prompt screen:

.. figure:: 445px-Win_putty_logged.png
   :align: center

   SSH connection via PuTTy

The last command prompt/terminal line should read as “root@rp-xxxxxx:~#“ (the default home directory on Red Pitaya is /root)

=====
Linux
=====

Start Terminal and type (replace IP address with the right one):

.. code-block:: shell-session

   user@ubuntu:~$ ssh root@192.168.1.100
   root@192.168.1.100's password: root
   Red Pitaya GNU/Linux/Ecosystem version 0.90-299
   redpitaya>

.. figure:: linux_terminal.png
   :align: center

=====
macOS
=====

Run terminal **Launchpad → Other → Terminal** and type (replace IP address with the right one):

.. code-block:: shell-session
  
   localhost:~ user$ ssh root@192.168.1.100
   root@10.0.3.249's password: root
   Red Pitaya GNU/Linux/Ecosystem version 0.90-299
   redpitaya>
