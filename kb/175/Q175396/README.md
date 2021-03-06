---
layout: page
title: "Q175396: Windows Socket Connection from a Multiple-Homed Computer"
permalink: /kb/175/Q175396/
---

## Q175396: Windows Socket Connection from a Multiple-Homed Computer

{% raw %}

	Article: Q175396
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): 2000,3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork win95 win98 win98se kbHardware
	Last Modified: 08-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 2000 Advanced Server 
	- Microsoft Windows 2000 Professional 
	- Microsoft Windows 2000 Server 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft Windows 98 Second Edition 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how a network adapter is chosen for an outbound Internet
	protocol (IP) datagram or stream of datagrams, and how a local source IP address
	is chosen for those datagrams on a multiple-homed computer.
	
	MORE INFORMATION
	================
	
	Because of the method that is used to determine this behavior, multiple-homed
	computers may send packets through one network adapter but use the source IP
	address of another network adapter in the computer. Some hardware or software
	firewall products may identify these packets as "spoofed," and therefore
	generate an IP spoofing error.
	
	This article applies specifically to programs that use the Windows Sockets
	interface to the TCP/IP stack.
	
	For additional information about how an outbound network adapter is chosen for
	programs that use NetBIOS over TCP/IP (such as file and print sharing), click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q166159 NetBIOS Connections from Multi-homed Computer
	
	The TCP/IP component of all Microsoft Windows operating systems is modeled on a
	"Weak End System" or a "Weak E/S" model. This model gives program developers the
	greatest amount of leeway when they design programs that use the network and are
	compatible with Microsoft products. This model also puts the responsibility of
	the behavior of the networking program on the developers, because the developers
	specify how the program accesses the TCP/IP stack and responds to incoming and
	outgoing frames.
	
	When a Windows Sockets program binds to a socket, one of the parameters that is
	passed in the bind() call is the local (source) IP address that should be used
	for outbound packets. Most programs do not have any knowledge of network
	topology, so they specify IPADDR_ANY instead of a specific IP address in their
	bind() call. IPADDR_ANY tells the stack that the program is going to let the
	stack choose the best local IP address to use; the program does not specify the
	local IP address.
	
	On a computer that has one network adapter, the IP address that is chosen is the
	IP address of the network adaptor in the computer. However, on a multiple-homed
	computer, the stack must make a choice. The stack cannot make an intelligent
	choice until it knows the target IP address for a Transmission Control Protocol
	(TCP) connection or a User Datagram Protocol (UDP) datagram.
	
	When the program sends a connect() call to a target IP address, or sends a send()
	call to a UDP datagram, the stack references the target IP address, and then
	examines the IP route table so that it can choose the best network adapter over
	which to send the packet. After this network adapter has been chosen, the stack
	reads the source IP address associated with that network adapter and uses that
	IP address as the source IP address for the outbound packets.
	
	If the program specifies a source IP address to use in the bind() call, that IP
	address is used as the source IP address for TCP connections or UDP datagrams
	sourced from that socket. However, the route table is still used to route the
	outbound IP datagrams, based on the target IP address. As a result of this
	behavior, the source IP address may not be the one associated with the network
	adapter that is chosen to send the packets.
	
	
	REFERENCES
	==========
	
	Request for Comments (RFC) 1122, section 3.3.4.2
	
	Additional query words: multi-homed multi homed Sonic
	
	======================================================================
	Keywords          : kbnetwork win95 win98 win98se kbHardware 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbWinNTS351search kbWinNTS350search kbWin95search kbWin98SEsearch kbWinAdvServSearch kbZNotKeyword3 kbWin98SE
	Version           : :2000,3.5,3.51,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
