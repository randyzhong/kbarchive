---
layout: page
title: "Q161775: Problem Starting Two Non-Queued TPs Simultaneously on Win3.x"
permalink: /kb/161/Q161775/
---

## Q161775: Problem Starting Two Non-Queued TPs Simultaneously on Win3.x

{% raw %}

	Article: Q161775
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.1,2.11
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.1, 2.11 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If the host allocates two conversations at the same time, causing two instances
	of a non-queued autostarted TP to be invoked on an SNA Server Windows 3.x
	client, the following sequence of events occurs:
	
	1. Two instances of the program are started.
	
	2. The first program issues a RECEIVE_ALLOCATE that completes after 20 or more
	  seconds, and normal data flow occurs.
	
	3. The second program issues a RECEIVE_ALLOCATE that fails with the following
	  error:
	
	  primary_rc = 0x0002 (AP_STATE_CHECK)
	  secondary_rc = 0x00000509 (AP_ALLOCATE_NOT_PENDING)
	
	  When this occurs, the first program stops responding.
	
	4. The computer running SNA Server may report the following events in the
	  Windows NT Application event viewer:
	
	  Event 60
	  Failed to invoke APPC TP <value>, sense data = X'084C0000'
	  AP_TRANS_PGM_NOT_AVAIL_NO_RETRY.
	
	  Event 557
	  DLOAD has timed out.
	
	  Event 575
	  Failed to Execute a program, RC=8 name=<value>.
	
	If there is a 30-second delay between host attach requests, the problem doesn't
	occur; both APPC TP's are invoked, and they run fine.
	
	CAUSE
	=====
	
	This is a problem in the SNA Server 2.11 Windows 3.x client. If the Windows 3.x
	client receives two dynamic load requests from two different servers within five
	seconds, the SNA client (Wdmod.dll) may send the second acknowledgement
	(RCV_ALLOC) message to the wrong server.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 2.1 and 2.11.
	This problem was corrected in the latest SNA Server version 2.11 U.S. Service
	Pack. For information on obtaining this service pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	A supported fix is now available, but has not been fully regression- tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ211 kbSNAServ210
	Version           : WINDOWS:2.1,2.11
	
	=============================================================================
	

{% endraw %}
