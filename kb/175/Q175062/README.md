---
layout: page
title: "Q175062: How To Determine from Which Computer a User Logged On"
permalink: /kb/175/Q175062/
---

## Q175062: How To Determine from Which Computer a User Logged On

{% raw %}

	Article: Q175062
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the methods available to identify from which system a
	user logged on. You may choose from one or more of the following methods:
	
	- Windows NT Auditing
	
	  -or-
	
	- Microsoft Network Monitor (or other network tracing utility)
	
	  -or-
	
	- Using the Windows Internet Naming Service (WINS) database
	
	  -or-
	
	- Using the NetBIOS Remote Name Cache table
	
	MORE INFORMATION
	================
	
	Windows NT Auditing
	-------------------
	
	To determine from which system a user logged on with Windows NT Auditing, perform
	the following steps:
	
	1. Start User Manager for Domains.
	
	2. Click Audit from the Policies menu.
	
	3. Click to enable Success for the Logon and Logoff category. Optionally, you
	  may also select the Failure check box.
	
	After the above procedure has been implemented, Windows NT will create an event
	log for each successful log on attempt. The log will appear like the example
	below:
	
	  Date:     10/13/97  Event ID:  528
	  Time:     10:32:11 AM  Source:  Security
	  User:     JoeSmith  Type:  Success Audit
	  Computer: MKTINGDOM  Category: Logon/Logoff
	
	  Description:
	  Logon/Logoff: Successful
	  Logon User Name: JoeSmith
	  Domain: MKTINGDOM
	  Logon ID: (0x0, 0x2D0D0)
	  Logon Type: 3
	  Logon Process: User32 Authentication Pkg:
	     MICROSOFT_AUTHENTICATION_PACKAGE_V1_0
	  Workstation Name: \\WKS2
	
	Network Monitor
	---------------
	
	To determine from which system a user logged on with Network Monitor, perform the
	following steps:
	
	1. Capture all incoming traffic to the domain controller(s). In order to reduce
	  the size of the captured data:
	
	   - If possible, include only the Primary or Backup Domain Controller that is
	     most likely to validate the intruder.
	
	   - Set a capture filter, including only the server message block (SMB)
	     protocol.
	
	   - Configure a large enough memory buffer through the Buffer Settings option
	     in the Capture menu.
	
	2. After the data has been captured, set a display filter to only include:
	
	  Protocol: SMB
	  Property: Account Name
	  Relation: Exists
	
	This will display all the initial SMB session setup containing the user name and
	the source media access control address.
	
	For example:
	
	Src Mac Addr: Dst Mac Addr: Description
	WKS1          SUNKING       C session setup & X, Username = MariaH, and C
	tree connect & X, Share = \\SUNKING\IPC$
	WKS2          SUNKING       C session setup & X, Username = JoeSmith, and C
	tree connect & X, Share = \\SUNKING\IPC$
	WKS3          SUNKING       C session setup & X, Username = Administrator,
	and C tree connect & X, Share = \\SUNKING\IPC$
	
	In the example above, WKS1 is the computer where the user is logging on from,
	SUNKING is the domain controller authenticating the request, and the Description
	contains the Windows NT domain account being used.
	
	NOTE: The Src Mac Addr may also been shown as a media access control or IP
	address if the NetBIOS name could not be resolved or the entry is not in the
	Network Monitor address database.
	
	Using the WINS Database
	-----------------------
	
	To determine from which system a user logged on using the WINS database, perform
	the following steps:
	
	1. Start WINS Manager.
	
	2. Click Show Database on the Mappings menu.
	
	3. Click Set Filter, type the user account name in the Computer Name criteria,
	  and then click OK.
	
	4. In the Mappings list, the entry with the user account name and the 03h
	  identifier maps to the IP address of the workstation from which the user
	  logged on to the domain.
	
	Using the NetBIOS Remote Name Table
	-----------------------------------
	
	To determine from which system a user logged on using the NetBIOS Remote Name
	Table, perform the following steps:
	
	1. From an MS-DOS command prompt, type the following, and then press Enter.
	
	  " net send <user name> "text message"" (without the quotation marks)
	
	  where <user name> is the user account for the user you are attempting to
	  locate.
	
	2. Type the following, and then press Enter.
	
	  " nbtstat -c" (without the quotation marks)
	
	3. As in the example above using the WINS Database, locate the user name that is
	  associated with the 03h identifier and the corresponding IP address is that
	  of the workstation.
	
	For more information, please refer to the following Microsoft Knowledge Base
	articles:
	
	ARTICLE-ID: Q157238
	TITLE : How to Activate Security Event Logging in Windows NT 4.0
	
	ARTICLE-ID: Q173939
	TITLE : How to Identify User Who Changed Administrator Password
	
	ARTICLE-ID: Q140714
	TITLE : Distinguishing Windows NT Audit Event Records
	
	Additional query words: secevent sec audit
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : WinNT:3.51,4.0
	Hardware          : x86
	
	=============================================================================
	

{% endraw %}
