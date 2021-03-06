---
layout: page
title: "Q318936: Event ID 3051 Is Caused by an Incorrect Netlogon Registry Key"
permalink: /kb/318/Q318936/
---

## Q318936: Event ID 3051 Is Caused by an Incorrect Netlogon Registry Key

{% raw %}

	Article: Q318936
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	If the Netlogon service does not start automatically and you cannot start it
	manually, you may see either of the following entries in Event Viewer:
	
	  WARNING: Netlogon Event 3051:
	  The registry or the information you just typed includes an illegal value for
	  "DBFlag".
	
	  -or-
	
	  WARNING: Netlogon Event 3051: The registry information you just typed
	  includes an illegal value for %1.
	
	CAUSE
	=====
	
	These error messages can occur if entries under the following registry key on
	the domain controller are missing, incorrect, or corrupted:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this issue, replace the Netlogon registry key with a copy from a
	working computer:
	
	1. On a working backup domain controller, start Registry Editor.
	
	2. Locate and then click the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon
	
	3. On the Registry menu, click Export Registry Key. Export the registry key to a
	  .reg file.
	
	4. Transfer the .reg file to the computer on which the Netlogon service cannot
	  start.
	
	5. Double-click the .reg file.
	
	6. When you are prompted to verify that you want to add the registry
	  information, click Yes.
	
	7. Click OK.
	
	8. Restart the server.
	
	MORE INFORMATION
	================
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q245086 Netlogon Event 3051, with Invalid Registry Entry in Event Viewer
	
	  Q258805 Event ID 3051 and 5706 on Domain Controllers
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
