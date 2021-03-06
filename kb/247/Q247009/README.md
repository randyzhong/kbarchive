---
layout: page
title: "Q247009: XIMS: Exchange Server 5.5 Post-SP3 Connector for cc:Mail Fixes"
permalink: /kb/247/Q247009/
---

## Q247009: XIMS: Exchange Server 5.5 Post-SP3 Connector for cc:Mail Fixes

{% raw %}

	Article: Q247009
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55kbfixlist
	Last Modified: 05-MAY-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article lists the article numbers for Microsoft Exchange Server version 5.5
	Connector for Lotus cc:Mail bugs that have been fixed since Exchange Server 5.5
	Service Pack 3 was released. For information about how to obtain the fixes
	listed in this article, click the article number next to the title of the
	article about that issue to view the article in the Microsoft Knowledge Base.
	
	NOTE: Exchange Server fixes for a particular component are cumulative and contain
	all of the previous fixes for that component. Fixes with a particular version
	number contain all of the fixes that have an earlier version number.
	
	MORE INFORMATION
	================
	
	The Connector for cc:Mail fixes include the following files:
	
	+-----------------------------+
	| File name | Current version | 
	+-----------------------------+
	| Ccmc.exe  | 5.5.2651.80     | 
	+-----------------------------+
	
	NOTE: The fix documented in Q249111, "XFOR: Exchange Connector for Lotus cc:Mail
	Not Supporting Korean Language," requires an updated Admin.exe file in addition
	to the updated Ccmc.exe file. This updated Admin.exe file is contained in new
	versions of the Administrator program, not the Exchange Connector for Lotus
	cc:Mail. Therefore, to fully resolve the problem documented in Q249111, you must
	obtain a new version of the Administrator program in addition to obtaining a new
	version of the Exchange Connector for Lotus cc:Mail.
	
	Fixes Released on March 7, 2000
	-------------------------------
	
	The following files are modified:
	
	- Ccmc.exe incremented to version 5.5.2651.80
	
	The following fixes are included:
	
	  Q249111 XFOR: Exchange Connector for Lotus cc:Mail Not Supporting Korean
	  Language
	  Q252819 XFOR: Read Receipt from cc:Mail Loses Content
	
	Fixes Released on November 23, 1999
	-----------------------------------
	
	The following files are modified:
	
	- Ccmc.exe incremented to version 5.5.2651.28
	
	The following fixes are included:
	
	  Q237588 XFOR: cc:Mail Connector Dirsync Problems with Multiple Exchange
	  Export Containers
	  Q237838 XADM: Exchange Server Corrupts Japanese cc:Mail Message Subject
	  Routing It to the Internet
	  Q241988 XFOR: After Dirsync, cc:Mail Address Does Not Include the Period After
	  the Middle Initial
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 kbfixlist
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
