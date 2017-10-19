---
layout: page
title: "Q176433: XADM: MIDSET Errors Generated by ISINTEG"
permalink: kb/176/Q176433/
---

## Q176433: XADM: MIDSET Errors Generated by ISINTEG

	Article: Q176433
	Product(s): Microsoft Exchange
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 22-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are running Microsoft Exchange Server version 5.0 and using ISINTEG to
	check the private information store, you may receive an error similar to the
	following during the reference count verification test:
	
	  Warning: Folder[0001-000000000144].Midset: Replid(4) misses some mids
	  Warning: Folder[0001-000000000144].Midset:
	  Name = Inbox, parentFID = 0001-000000000141,
	  rootFID = 0001-000000000140
	  ptagSegmentStart = 0001-00000000070C, ptagSegmentIndex = 4, #messages =
	  3, #sub-folders = 1
	  Missing interval = [0004-000000000001, 0004-00000001000D]
	
	These fixes may affect the ability of users using OST's to synchronize their
	folders.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.0. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.0. For information on obtaining the Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	