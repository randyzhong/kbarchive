---
layout: page
title: "Q226538: TCP/IP Clients Lose Connections To Multihomed SNA Server"
permalink: /kb/226/Q226538/
---

## Q226538: TCP/IP Clients Lose Connections To Multihomed SNA Server

{% raw %}

	Article: Q226538
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,2.11SP1,2.11SP2,3.0,3.0SP1,3.0SP2,3.0SP3,4.0,4.0SP1,4.0SP2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11SP1, 2.11SP2, 3.0, 3.0SP1, 3.0SP2, 3.0SP3, 4.0, 4.0SP1, 4.0SP2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Clients using TCP/IP to connect to an SNA Server are able to establish a
	session, but intermittently, the client session is lost. When this happens, the
	following event is logged at the server:
	
	  Event ID: 706
	  Source: SNA Server
	  Description:
	  Connection to client xxx.xxx.xxx.xxx:xxxx has been aborted due to too many
	  (100) pending writes.
	
	In a 3270 terminal session, users may lose their connections to the mainframe
	application and be sent back to the VTAM Logon screen.
	
	CAUSE
	=====
	
	This problem can occur if the computer running Windows NT Server has the TCP/IP
	transport bound to multiple network interface cards (NICs), which are connected
	to different (disparate) networks. When trying to send a message, if TCP/IP
	detects a problem with the route between the server and the client, the
	transport is designed to use a secondary NIC to send the message. This works
	fine as long as the secondary NIC is connected to a network with a working route
	to the client. But if the secondary NIC is on a disparate network, the server
	message will not reach the client, causing the TCP/IP connection to timeout and
	drop.
	
	Please note that this is only one situation where an Event 706 may be generated
	by Microsoft SNA Server.
	
	RESOLUTION
	==========
	
	Disable the TCP/IP protocol binding from the adapters where it is not needed.
	For example, many SNA Servers have one or more Ethernet adapters to support
	TCP/IP client connections, and one or more Token Ring adapters to support DLC
	connections between the server and a mainframe or AS/400. In this scenario,
	because TCP/IP is not needed on the Token Ring adapter, it should be disabled
	from this adapter.
	
	MORE INFORMATION
	================
	
	When Microsoft Network Monitor is installed on the SNA Server, and network
	traffic is captured on both NICs, you can observe the server receiving client
	traffic over one card and responding back over the other card. The TCP/IP stack
	switches to the alternate card when it believes the first card is busy.
	
	For additional information about running Microsoft Windows NT Server on
	multihomed computers, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q139960 Limiting LAN Traffic to One Network Adapter
	
	  Q157025 Default Gateway Configuration for Multihomed Computers
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ200 kbSNAServ211 kbSNAServ400 kbSNAServ210
	Version           : WINDOWS:2.0,2.1,2.11,2.11SP1,2.11SP2,3.0,3.0SP1,3.0SP2,3.0SP3,4.0,4.0SP1,4.0SP2
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
