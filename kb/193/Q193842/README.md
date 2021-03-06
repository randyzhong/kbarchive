---
layout: page
title: "Q193842: XFOR: DXA Does Not Handle Long MAC Mail Addresses Properly"
permalink: /kb/193/Q193842/
---

## Q193842: XFOR: DXA Does Not Handle Long MAC Mail Addresses Properly

{% raw %}

	Article: Q193842
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.5
	Operating System(s): 
	Keyword(s): exc55sp2fix
	Last Modified: 09-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange DXA does not ensure that Mail ALIAS (MAILBOX) names are
	truncated to 10 characters. Furthermore, the DXA does not remove invalid
	characters such as a comma.
	
	If the total length of the user's alias is more than 10 characters, the names are
	discarded and never included in directory synchronization (dirsynch) operations.
	The application log shows an error and a warning for each name it discards. For
	example:
	
	  Event: 247
	  Source: MSExchangeDX
	  Type: Error
	  Category: MS Mail 3.2
	  Description: The e-mail address of the following transaction is not a
	  valid format. See previous events logged by the Microsoft Exchange
	  System Attendant component for details. The transaction is A User02,
	  MacGroovy@GroovyMac MSMAIL:User02, MacGroovy@GroovyMac. (Thread 0)
	
	  Event: 5
	  Source: MSProxy
	  Type: Warning
	  Category: none
	  Description: Microsoft Mail address failure. The Mailbox name
	  'MS:Microsoft/testproxy/User02, MacGroovy' is not valid. There must be
	  1-10 valid characters.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: Directory Synchronization (Dirsync)
	
	  File Name   Version
	  ----------------------
	  Dxa.exe     5.5.2405.0
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5 for Windows NT. This problem was first corrected in Exchange Server
	5.5 Service Pack 2.
	
	======================================================================
	Keywords          : exc55sp2fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : WinNT:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
