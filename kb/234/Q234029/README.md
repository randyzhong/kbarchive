---
layout: page
title: "Q234029: Err Msg: &quot;Temp Directory Not Accessible&quot; After Applying TSE SP4"
permalink: /kb/234/Q234029/
---

## Q234029: Err Msg: &quot;Temp Directory Not Accessible&quot; After Applying TSE SP4

{% raw %}

	Article: Q234029
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0 SP4
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 SP4, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you apply Windows NT Server 4.0, Terminal Server Edition Service Pack 4
	(SP4), error messages similar to the following may be displayed:
	
	  temp directory not accessible
	
	CAUSE
	=====
	
	This behavior occurs because Terminal Server SP4 does not reset the permissions
	or delete existing temporary folders that are orphaned after a dirty shutdown.
	This behavior change was added in SP4 to improve security by preventing new
	users from viewing work that may have been abandoned by previous sessions
	because of a dirty shutdown.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	WORKAROUND
	==========
	
	For additional information on how to work around this behavior, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q186516 Terminal Server Commands: FLATTEMP
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT Server 4.0, Terminal
	Server Edition. This problem was first corrected in Windows NT Server 4.0,
	Terminal Server Edition, Service Pack 5.
	
	MORE INFORMATION
	================
	
	Normally, Terminal Server session temporary folders are removed by WINLOGON when
	a user logs off or the session is reset. However, a dirty shutdown orphans the
	temporary directories for any active or disconnected sessions. A dirty shutdown
	occurs when the server crashes because of hardware problems, software problems,
	or power disruption. In addition, a regression introduced in SP4 winlogon may
	cause a dirty shutdown when a server is restarted without a user logged on to
	the console.
	
	Note that the hotfix listed in this article does not address the issue of folders
	not being deleted at logoff; it only ensures that if the folder already exists
	and a user logging on gets assigned the same temporary folder, that permissions
	for the existing folder will be set correctly for the new user. EMP folders may
	still exist.
	
	For more information, please see the following Microsoft Knowledge Base article:
	
	  230449 Service Control Handler May Not Receive SERVICE_CONTROL_SHUTDOWN
	  Notification
	
	Additional query words: wts tse terminalsrv
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400sp4 kbNTTermServSearch
	Version           : winnt:4.0 SP4
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
