---
layout: page
title: "Q163837: SNMP Query to Windows NT Returns Same Value for NTS and NTW"
permalink: /kb/163/Q163837/
---

## Q163837: SNMP Query to Windows NT Returns Same Value for NTS and NTW

{% raw %}

	Article: Q163837
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbSDKPlatform kbSNMP kbGrpDSNetkbbuglist kbfixlist
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use an SNMP utility to obtain the system type from a computer running
	Windows NT, the value returned is the same for both Windows NT Server and
	Windows NT Workstation. The system types appear to be identical.
	
	Because Windows NT workstations and servers have different capabilities, it is
	necessary to differentiate between these versions of Windows NT, especially when
	managing a large network. In addition, it is necessary to differentiate between
	Windows NT Servers and Domain Controllers, since they also have different roles
	in the domain model.
	
	CAUSE
	=====
	
	The SysObjectID field (1.3.6.1.4.1.311.1.1.3.1) returned by the computer running
	Windows NT is the same if the computer is running Windows NT Server or Windows
	NT Workstation.
	
	RESOLUTION
	==========
	
	A change was made in Windows NT 4.0 Service Pack 2 (SP2) and Windows NT 3.51
	post-SP5 to the SNMP components so that the different system types are now
	reported as follows:
	
	  1.3.6.1.4.1.311.1.1.3.1.1 for Windows NT Workstation
	  1.3.6.1.4.1.311.1.1.3.1.2 for Windows NT Servers
	  1.3.6.1.4.1.311.1.1.3.1.3 for Windows NT Domain Controllers
	
	This enables the user of the SNMP utility to more precisely identify the type of
	Windows NT system.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Windows NT version
	4.0. This problem was corrected in the latest Microsoft Windows NT 4.0 U.S.
	Service Pack. For information on obtaining the service pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. A
	supported fix is now available, but is not fully regression-tested and should be
	applied only to systems experiencing this specific problem. Unless you are
	severely impacted by this specific problem, Microsoft recommends that you wait
	for the next Service Pack that contains this fix. Contact Microsoft Product
	Support Services for more information.
	
	
	Additional query words: prodnt manager intel landesk hp openview insight insite OID
	
	======================================================================
	Keywords          : kbnetwork kbSDKPlatform kbSNMP kbGrpDSNet kbbuglist kbfixlist
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : winnt:3.51,4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
