MAC-Telnet / MAC SSH for Linux
==============================

Open source MAC Telnet client and server for connecting to Mikrotik RouterOS 
routers and Linux machines via MAC address. 
             
Based on [MAC-Telnet](https://github.com/haakonnessjoen/MAC-Telnet) 
the original work of 
[haakonnessjoen](https://github.com/haakonnessjoen) (_Håkon Nessjøen_).
The original version implements the following:

* A linux console tool for connecting to _MikroTik RouterOS_ devices via their
  ethernet address.
* Linux daemon that implements the _MAC Telnet_ Daemon to permit connecting
  to Linux machines via their ethernet address.

Forked to implement additional functionality for tunneling any TCP connection 
trough the _MAC Telnet_ protocol. The main use case is connecting to Linux 
machines via their ethernet address using _SSH_ protocol for security.

The server supports two modes of operation:
* Standard MAC-Telnet Server Mode
* TCP Connection Forwarding Mode: Tunnels a TCP connection to a local port on 
  the client to a specific local port on the server side through MAC-Telnet 
  protocol. This mode of operation is used for forwarding SSH connections 
  through the MAC-Telnet protocol.

The client supports three modes of operation:
* Standard MAC-Telnet Client Mode
* TCP Connection Forwarding Mode: Tunnels a specific local port on the client to 
  the server through MAC-Telnet protocol.
* SSH Forwarding Mode: The client takes care of setting up the tunnel and 
  launching the SSH client. 

The _MAC-Telnet_ and _Forwarding_ modes of operation are _not_ compatible. Both 
the client and the server must operate in the same mode for successful 
communications. The _SSH Forwarding Mode_ has the following advantages in comparison to standard
_MAC-Telnet_:

* The_mactelnet.users_ configuration file is not needed. Instead of maintaining 
  another set of user passwords for _MAC-Telnet_, the standard authentication 
  mechanisms supported by ssh are used.
* Public key authentication works seamlessly permiting logins without password.
* The communication between client and server is encrypyted by _SSH_.
* The daemon does not require root privileges and can be run by a non-privileged 
  user for additional security. In case the _-n_ option is used the daemon, the
  command must be run as _root_ user, but the_-U_ option can be used to drop
  privileges once the initial setup phase ends.
* The daemon relies on the security model of _SSH_, instead of creating a shell
  environment itself.


For information on other projects you can check 
my [GitHub Personal Page](http://aouyar.github.com)
and [GitHub Profile](https://github.com/aouyar).


Documentation
-------------

Check the website for the original project 
[MAC-Telnet](https://github.com/haakonnessjoen/MAC-Telnet) 
by 
[haakonnessjoen](https://github.com/haakonnessjoen) (_Håkon Nessjøen_)
for the official documentation of the project.

The documentation for the forked version with the experimental features is 
published at [MAC-Telnet Project Web Page](http://aouyar.github.com/MAC-Telnet/)
by [Ali Onur Uyar]({{ page.baseptr}}/) 
([{{ site.user }} @ GitHub] (https://github.com/{{ site.user }})).


Licensing
---------

_PyMunin_ is copyrighted free software made available under the terms of the 
_GPL License Version 3_ or later.

See the _LICENSE_ file that acompanies the code for full licensing information.