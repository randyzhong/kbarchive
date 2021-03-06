---
layout: page
title: "Q149422: XCON: Creating Crash Dump Files when MTA Encounters Fatal Errors"
permalink: /kb/149/Q149422/
---

## Q149422: XCON: Creating Crash Dump Files when MTA Encounters Fatal Errors

{% raw %}

	Article: Q149422
	Product(s): Microsoft Exchange
	Version(s): 4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbenv kbusage exc4 exc5 exc55
	Last Modified: 14-FEB-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to cause the Microsoft Exchange Server message
	transfer agent (MTA) to create a crash dump file when a fatal error occurs
	instead of stopping unexpectedly.
	
	MORE INFORMATION
	================
	
	When the message transfer agent (MTA) encounters a fatal error on a computer
	running Microsoft Exchange Server, the MTA normally stops unexpectedly. When
	this occurs, a severity 16 event appears in the event log and the Services tool
	in Control Panel indicates that the MSExchangeMTA service has stopped.
	
	For troubleshooting purposes, you may want to configure Windows NT so that the
	MTA creates a crash dump file when a fatal error occurs instead of stopping
	unexpectedly. To do so, use the following steps.
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	1. Verify that Dr. Watson for Windows NT is configured correctly. To do so,
	  follow these steps:
	
	  a. Click Start, click Run, type "drwtsn32 -i" (without the quotation marks)
	     in the Open box, and then click OK.
	
	  b. Click OK again.
	
	  c. Click Start, click Run, type "drwtsn32" (without the quotation marks) in
	     the Open box, and then click OK.
	
	  d. Verify that the Create Crash Dump File check box is selected.
	
	  e. Verify that the locations in the Log File Path and Crash Dump boxes refer
	     to the Windows NT folder. In Dr. Watson for Windows NT, the Windows NT
	     folder is typically represented by the %windir% variable.
	
	  f. Click the Visual Notification check box to clear it. This allows the MTA
	     to create the crash dump file without any input from you. If this check
	     box is selected, a dialog box is displayed when a fatal error occurs and
	     the crash dump file is not created until the dialog box is closed.
	
	  g. Click OK to close Dr. Watson for Windows NT.
	
	After you perform these steps, the following registry values exist:
	
	     Value name: Auto
	     Value type: REG_SZ
	     Value data: 1
	
	     Value name: Debugger
	     Value type: REG_SZ
	     Value data: drwtsn32.exe -p %ld -e %ld -g
	
	     Value name: UserDebuggerHotKey
	     Value type: REG_DWORD
	     Value data: 0
	
	These values are located under the following registry key:
	
	     HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\Current Version
	     \Aedebug
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	2. Start Registry Editor (Regedt32.exe or Regedit.exe as appropriate for your
	  version of Windows NT).
	
	3. Locate the following registry key:
	
	     HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSExchangeMTA
	     \Parameters
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	4. On the Edit menu, click Add Value, and then add the following registry value
	  (note case sensitivity):
	
	     Value name: Raise Exception on fatal error
	     Value type: REG_DWORD
	     Value data: 1
	
	After you perform these steps, the MTA does not stop unexpectedly when a fatal
	error occurs. Instead, fatal errors generate exceptions and cause a crash dump
	file to be created. The exception generated is 0xE005<xxxx>, where
	<xxxx> is a number that represents the specific error that occurred, if
	appropriate.
	
	Additional query words: 9405
	
	======================================================================
	Keywords          : kbenv kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : :4.0,5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
