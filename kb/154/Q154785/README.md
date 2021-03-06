---
layout: page
title: "Q154785: WinNT 3.51 Service Packs (SPs) Incorrectly Update Newer SPs"
permalink: /kb/154/Q154785/
---

## Q154785: WinNT 3.51 Service Packs (SPs) Incorrectly Update Newer SPs

{% raw %}

	Article: Q154785
	Product(s): Microsoft Windows NT
	Version(s): 3.51
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.51 
	- Microsoft Windows NT Server version 3.51 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	It is possible to replace a newer version of a Service Pack for Windows NT 3.51
	with an older version. This is not intended behavior.
	
	CAUSE
	=====
	
	Version information was not updated for Service Packs 1, 2, 3 and 4 for Windows
	NT 3.51. It is possible for any of these service packs to install over a newer
	service pack.
	
	RESOLUTION
	==========
	
	Windows NT will now detect that a newer-version Service Pack is installed and
	not install an older Service Pack over the newer version.
	
	Note: If Service Pack 3 is installed over Service Pack 4, please refer to the
	following article in the Microsoft Knowledge Base:
	
	Q148262Removing Windows NT 3.51 SP 4 May Cause Logon Failures
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem with Windows NT version 3.51
	Service Packs 1, 2, 3, and 4. This problem was corrected in the latest Windows
	NT 3.51 U.S. Service Pack. For information on obtaining the Service Pack, query
	on the following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS351search
	Version           : 3.51
	
	=============================================================================
	

{% endraw %}
