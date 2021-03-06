---
layout: page
title: "Q160392: Systems with 4 GB or More of RAM Cannot Boot Windows NT 4.0"
permalink: /kb/160/Q160392/
---

## Q160392: Systems with 4 GB or More of RAM Cannot Boot Windows NT 4.0

{% raw %}

	Article: Q160392
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Systems with 4 GB or more of RAM will fail to boot. The system fails with a stop
	message 0x0000003f NO_MORE_SYSTEM_PTES.
	
	WORKAROUND
	==========
	
	This has been fixed in Ntoskrnl.exe in Windows NT 4.0 Service Pack 2 and later.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.00. This
	problem has been corrected in the latest U.S. Service Pack for Windows NT
	version 4.00. For information on obtaining the Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	Windows NT 4.0 may also not install on a computer with 4 GB of RAM installed. A
	STOP 0x0000003f may occur during installation. To resolve this issue, use the
	following methods:
	
	- Remove 2 GB of the physical RAM, install Windows NT, apply SP3, and then
	  reinstall the physical RAM.
	
	- If the STOP 0x0000003f occurs during the GUI-mode portion of Setup, the
	  installation can be halted immediately prior to the GUI mode portion and the
	  /maxmem switch can be used in the Boot.ini file. For additional information
	  about this switch, please see the following article in the Microsoft
	  Knowledge Base:
	
	  Q108393 MAXMEM Option in Windows NT BOOT.INI File
	
	Additional query words: prodnt 0x0000003f RAM OUT_OF_PTES
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
