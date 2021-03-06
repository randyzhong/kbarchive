---
layout: page
title: "Q214467: Windows NT 4.0 DNR Only &quot;Devolves&quot; Two Domain Suffixes"
permalink: /kb/214/Q214467/
---

## Q214467: Windows NT 4.0 DNR Only &quot;Devolves&quot; Two Domain Suffixes

{% raw %}

	Article: Q214467
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When a user tries to connect a Windows NT 4.0 client computer to a server that
	is more than two levels higher in the domain name tree structure, the user may
	find it necessary to type the full domain name to connect. This is caused by the
	client computer domain name resolver component (DNR) only "devolving" two domain
	suffixes.
	
	For instance, if you have a client named
	
	  mycomputer.subdomain3.subdomain2.subdomain1.example.microsoft.com
	
	the domain suffix is
	
	  subdomain3.subdomain2.subdomain1.example.microsoft.com
	
	If you want to ftp to a server named "myserver.example.microsoft.com," it is
	necessary to type the full name "myserver.example.microsoft.com." to connect.
	
	If you type only "myserver", the client queries the DNS for the following:
	
	  myserver.subdomain3.subdomain2.subdomain1.example.microsoft.com
	  myserver.subdomain2.subdomain1.example.microsoft.com (one level of
	  devolution)
	  myserver.subdomain1.example.microsoft.com (two levels of devolution)
	
	CAUSE
	=====
	
	The DNR component was designed to only devolve two levels up the domain suffix.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Windows NT service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  
	  +---------------------------------------------------+
	  | Date     | Time   | Size   | File Name | Platform | 
	  +---------------------------------------------------+
	  | 01/07/99 | 05:01p | 42,768 | rnr20.dll | (x86)    | 
	  +---------------------------------------------------+
	  | 01/07/99 | 05:11p | 43,792 | rnr20.dll | (Alpha)  | 
	  +---------------------------------------------------+
	
	
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	With the default settings, it continues to devolve only two levels. However, this
	hotfix supports the new MaxDomainsSearchListSize registry value to make the
	devolution behavior configurable:
	
	  Registry value:
	  HKLM\System\CurrentControlSet\Services\Tcpip\Parameters\MaxDomainsSearchListSize
	
	  Value Type: REG_DWORD
	  Default: 3 (including the first query with no devolution)
	  Range:1-12 (decimal)
	
	CAUTION: Setting this value higher than necessary can cause delays in name
	resolution, as more attempts to locate the name are made.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0.
	
	Additional query words: 4.00
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
