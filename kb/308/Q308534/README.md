---
layout: page
title: "Q308534: Streets and Trips 2002: Err Msg When Using Find Feature"
permalink: /kb/308/Q308534/
---

## Q308534: Streets and Trips 2002: Err Msg When Using Find Feature

{% raw %}

	Article: Q308534
	Product(s): Microsoft Automap
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbimu
	Last Modified: 15-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Streets & Trips 2002, version 1.0, used with:
	   - the operating system: Microsoft Windows 98 
	   - the operating system: Microsoft Windows 98 Second Edition 
	   - the operating system: Microsoft Windows Millennium Edition 
	-------------------------------------------------------------------------------
	
	*********************************************************************
	**                           - WARNING -                           **
	**     THE INFORMATION BELOW IS PRELIMINARY AND HAS NOT BEEN       **
	**     CONFIRMED OR TESTED BY MICROSOFT. USE ONLY                  **
	**     WITH DISCRETION.                                            **
	*********************************************************************
	
	SYMPTOMS
	========
	
	When you attempt to use the Find feature in Microsoft Streets and Trips 2002,
	you may receive an error message similar to the following:
	
	  Streets and Trips has encountered a problem and needs to close.
	
	When you click Details, the following information is displayed:
	
	Application unable to continue running due to an internal error
	(6-40028--1073741680) 
	
	Error signature appname: streets.exe appver: 9.0.16.2001 modname: MSVCRT.DLL modver: 6.0.8397.0 offset: 0002CD03
	
	CAUSE
	=====
	
	This problem can occur when there is a line of code in the Win.ini file that
	interferes with the Find feature of Streets and Trips.
	
	
	WORKAROUND
	==========
	
	To resolve this issue, do one of the following methods.
	
	Method 1
	--------
	
	To work around this problem, restart your computer with the Process Win.ini file
	option turned off. To do this, follow these steps:
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "msconfig" (without the quotation marks), and then
	  click OK.
	
	3. In the System Configuration Utility dialog box, click "Selective startup",
	  and then click to clear the Process Win.ini check box.
	
	4. Click OK to close the System Configuration Utility dialog box.
	
	  When you receive the confirmation message, click Yes.
	
	5. Restart your computer.
	
	6. Start Streets and Trips.
	
	7. After you complete your task in Streets and Trips, turn on the Process
	  Win.ini file option.
	
	NOTE: You need to repeat these steps each time that you want to use the Find
	feature of Streets and Trips.
	
	Method 2
	--------
	
	You may also be able to resolve this issue by removing your existing printer
	driver, and then downloading and installing the latest version of the printer
	driver available for your printer. To do this, follow these steps:
	
	1. Click Start, point to Settings, click Control Panel, and then double-click
	  Add/Remove Programs.
	
	2. On the Install/Uninstall tab, select your printer driver (if it is displayed
	  in the list), and then click Add/Remove.
	
	3. Click Yes when you receive the following message:
	
	  Are you sure you want to completely remove the program and all of its
	  components?
	
	4. Click Start, point to Settings, and then click Printers.
	
	5. Right-click the printer that you want to remove, and then click Delete.
	
	6. Click Yes when you receive the following message:
	
	  Are you sure you want to delete the printer?
	
	7. Restart your computer.
	
	8. Download and install the latest driver for your printer. Contact your printer
	  manufacturer to inquire about how to obtain and install the latest driver for
	  your printer.
	
	NOTE: If you are experiencing this error message on a Microsoft Windows XP Home
	or Professional operating system, you must install updated drivers that are
	specifically designed to work with Windows XP. Drivers designed to work with
	previous operating systems will not function correctly on Windows XP.
	
	For information about how to contact , click the appropriate article number below
	to view the article in the Microsoft Knowledge Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	  Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbimu 
	Technology        : kbHomeProdSearch kbExpediaSearch kbExpediaStreets2002
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
