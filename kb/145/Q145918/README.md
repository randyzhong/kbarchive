---
layout: page
title: "Q145918: FP: HTTP Error 400 Opening FrontPage Explorer"
permalink: /kb/145/Q145918/
---

## Q145918: FP: HTTP Error 400 Opening FrontPage Explorer

{% raw %}

	Article: Q145918
	Product(s): Word Front Page
	Version(s): windows:1.0,1.1,97
	Operating System(s): 
	Keyword(s): kberrmsg kbusage kbdta
	Last Modified: 04-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows with Bonus Pack 
	- Microsoft FrontPage for Windows, versions 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 98 version of this article, see Q194058.
	
	SYMPTOMS
	========
	
	When you open FrontPage Explorer and click the List Webs button in the Open Webs
	dialog box or create a new Web, you get an HTTP 400 error message.
	
	CAUSE
	=====
	
	This error indicates insufficient memory due to one or more of the following:
	
	- Not enough physical Random Access Memory (RAM).
	- Insufficient free space on your hard disk drive.
	- Not enough virtual memory.
	- Invalid or no Temp directory.
	
	RESOLUTION
	==========
	
	To resolve this error, do the following:
	
	1. Make sure that you have at least 16 megabytes (MB) of physical RAM installed
	  on your computer if you are running the Personal Web Server, FrontPage
	  Explorer, and FrontPage Editor at the same time. If you are not running the
	  Personal Web Server, but you are running FrontPage Explorer and FrontPage
	  Editor, make sure your computer has at least 8 MB of physical RAM.
	
	2. Verify that you have at least 16 MB of free space on the hard disk.
	
	3. Make sure that you have a permanent swap file that is at least 20 MB.
	
	4. Check that there is a valid SET TEMP statement in the Autoexec.bat file. Also
	  make sure that the Temp directory exists and is not full of temporary files.
	  Microsoft recommends that you delete these temporary files after you exit
	  Windows.
	
	Additional query words: 1.00a front page personal Web server pws explorer editor out of memory insufficient low not enough vermeer
	
	======================================================================
	Keywords          : kberrmsg kbusage kbdta 
	Technology        : kbFrontPageSearch kbFrontPage1xSearch kbFrontPage97Search kbZNotKeyword3 kbFrontPage100 kbFrontPage110
	Version           : windows:1.0,1.1,97
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
