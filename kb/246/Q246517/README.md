---
layout: page
title: "Q246517: XADM: Unable to Resolve DL from the Global Address List"
permalink: /kb/246/Q246517/
---

## Q246517: XADM: Unable to Resolve DL from the Global Address List

{% raw %}

	Article: Q246517
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When a client tries to resolve a name and the organization created a
	distribution list (DL) with the name "SM," "SMT," or "SMTP" (without quotation
	marks), the client receives all users with an Simple Mail Transfer Protocol
	(SMTP) address from the Global Address List as possible candidates in the name
	resolution.
	
	CAUSE
	=====
	
	This problem occurs when an organization creates a mailbox or DL with the
	letters "SMTP" (without quotation marks) or a shortened version, such as "SMT,"
	"SM," or "S" (without quotation marks).
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	To resolve this issue:
	
	1. Click Start, click Run, and then type "regedt32.exe" (without the quotation
	  marks).
	
	2. Locate and click the following registry key:
	
	  HKEY_LOCAL_MACHINE/System/CurrentControlSet/Services/MSExchangeDS/Parameters
	
	3. On the Edit menu, click Add Value, and then add the following Value Name and
	  Data Type:
	
	  Value Name: DSA Heuristics
	  Data Type: Reg_SZ
	
	4. Click OK, type "00010" (without the quotation marks) for the string value,
	  and then click OK.
	
	Follow these steps for each server in the organization.
	
	NOTE: You must restart Directory Services for these changes to take effect.
	
	MORE INFORMATION
	================
	
	Exchange interprets S, SMT, and SMTP as an improperly typed one-off addresses,
	and then presents the entire Global Address List for the recipient. If you set
	up a DL and users have aliases of SMT (SMTP), CCM (cc:Mail), PRO (Profs), SNA
	(SNADS), and not (Notes), it works in the same way. However, if you type "=CCM"
	(without the quotation marks) in the To box, and then resolve the name, the name
	resolves to the correct address.
	
	Additional query words: GAL
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
