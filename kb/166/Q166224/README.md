---
layout: page
title: "Q166224: SNA Server 802.2 Connection Fails to Reactivate"
permalink: /kb/166/Q166224/
---

## Q166224: SNA Server 802.2 Connection Fails to Reactivate

{% raw %}

	Article: Q166224
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.51 (all service packs),4.0 SP1,4.0 SP2
	Operating System(s): 
	Keyword(s): kbnetworkkbbuglist kbfixlist
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51 (all service packs), 4.0 SP1, 4.0 SP2 
	- Microsoft Windows NT Workstation versions 3.51 (all service packs), 4.0 SP1, 4.0 SP2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If an SNA Server 802.2 connection (over Token Ring, Ethernet or FDDI) is
	manually stopped or fails due to an outage, the connection may stop responding
	(hang) in an incoming or inactive status and cannot be reactivated until the SNA
	Server service is stopped and restarted. When attempting to restart the
	connection, the status will remain as incoming or inactive, and will never
	indicate a pending status.
	
	If multiple connections all share the same 802.2 link service, this problem may
	only affect a single connection.
	
	This problem can also occur when connecting a branch-based remote link service
	through an 802.2 distributed link service running on a centralized server,
	though the behavior within SNA Admin or Manager is different. The remote link
	service may indicate a pending status when it is restarted.
	
	To confirm this problem using SNA Server tracing, a Level 2 message trace on the
	802.2 link service (for example, snadlc1, snadlc2 and so on) is required. This
	trace will indicate a call to data link control (DLC) close station which never
	completes.
	
	For information about a problem that has similar symptoms, but a different cause,
	please see the following article in the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q147514
	  TITLE : Stopping SNA Server Service Causes Perpetual "Stopping" Status
	
	The problem in the referenced article occurs only Windows NT version 3.51 whereas
	the problem documented here occurs on both Windows NT version 3.51 and 4.0.
	
	
	CAUSE
	=====
	
	When an 802.2 connection is shut down, the SNA Server link service submits a
	DLC.CLOSE.STATION request to the Windows NT Dlc.sys driver. If the link station
	is in a checkpoint state within the Windows NT DLC driver (where the t1 or ti
	timer has expired for the link station), the DLC.CLOSE.STATION attempt will
	never complete. Because the link station has not completed the shutdown process,
	the SNA Server link service is not able to reactivate the connection.
	
	RESOLUTION
	==========
	
	A hotfix to Windows NT 3.51 and 4.0 is available to correct this problem. To
	resolve this problem, obtain the hotfix mentioned below.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 3.51, Windows NT 3.51
	(SP1-SP5), and Windows NT 4.0 (SP1, SP2). This problem was corrected in the
	latest Microsoft Windows NT 4.0 U.S. Service Pack. For information on obtaining
	the service pack, query on the following word in the Microsoft Knowledge Base
	(without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words: prodnt 4.00 3.51 2.0 2.1 2.11 3.0
	
	======================================================================
	Keywords          : kbnetwork kbbuglist kbfixlist
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTW400sp2 kbWinNTW400sp1 kbWinNTSsearch kbWinNTS400sp2 kbWinNTS400sp1 kbWinNTS400search
	Version           : winnt:3.51 (all service packs),4.0 SP1,4.0 SP2
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
