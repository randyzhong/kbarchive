---
layout: page
title: "Q152234: XCLN: Exchange Client for Windows 95 Starts Very Slowly"
permalink: /kb/152/Q152234/
---

## Q152234: XCLN: Exchange Client for Windows 95 Starts Very Slowly

{% raw %}

	Article: Q152234
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 28-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Exchange client for Windows 95 might load slowly, or appear to
	hang, if DNS is enabled for TCP/IP and no DNS server is available. This might
	happen if a physical adapter is installed that does not use DNS and there is a
	Dial-Up Adapter that uses DNS.
	
	In Windows 95, the DNS setting is valid for all adapters that are present. You
	cannot turn off DNS for one adapter and leave it on for another. It might be
	necessary to manually disable DNS when switching between network adapters in
	order for the Microsoft Exchange client for Windows 95 to load without a delay.
	
	MORE INFORMATION
	================
	
	The Domain Name System (DNS) is used to identify computers on the Internet.
	Windows 95 supports more than one network adapter for TCP/IP. The Dial-Up
	Adapter allows Windows 95 to use a modem as a network adapter that can be used
	to connect to the Internet with TCP/IP.
	
	Usually, when connecting to the Internet with a Dial-Up Adapter, a DNS server
	will be used as configured by choosing TCP/IP and the Dial-Up Adapter in the
	Network applet of the Control Panel. However, enabling this setting for the
	Dial-Up Adapter also enables it for all other adapters configured to use
	TCP/IP.
	
	If one adapter cannot access DNS, it will be necessary to disable DNS when using
	that adapter. For example, if you use WINS for name resolution when at work, but
	DNS when you connect to the Internet through Dial-Up networking, you will need
	to disable DNS when at work. Re-enable DNS when you connect to the Internet
	through Dial-Up networking.
	
	The slowness may also be seen when a normally available DNS server is not
	available. If you are not able to disable DNS, wait a few minutes for the
	Microsoft Exchange client for Windows 95 to load after DNS fails.
	
	
	Additional query words: smtp
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
