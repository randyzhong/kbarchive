---
layout: page
title: "Q200474: XADM: Unable to Create More than One Server Location"
permalink: /kb/200/Q200474/
---

## Q200474: XADM: Unable to Create More than One Server Location

{% raw %}

	Article: Q200474
	Product(s): Microsoft Exchange
	Version(s): 5.0,5.5
	Operating System(s): 
	Keyword(s): exc5 exc55
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article explains the functions and limitations involved when you use Server
	Locations in the Microsoft Exchange Server Administrator program.
	
	MORE INFORMATION
	================
	
	You can only have one entry in the Server Location section on the <Server>
	Properties in the Exchange Administrator program.
	
	Users can access public folder replicas more efficiently if you group servers
	within a site into locations. You can also use locations to limit the scope of
	users who can access the services of a connector.
	
	Exchange Server automatically searches for public folder replicas within its own
	location. If it can't locate the public folder replica in its own location, it
	searches servers outside of the location. If you want users to access public
	folder replicas on certain servers by default, you can create a wildcard
	location called asterisk (*). Exchange Server searches for public folder
	replicas on * servers unless you've specified another location for accessing the
	public folder replicas. To create a wildcard location:
	
	1. Type or select the name in the Server Location box.
	
	2. To add a server to *, type an asterisk, "*" (without the quotation marks) in
	  the Server Location box.
	
	For additional information on which public folder replica is used, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q154941 XADM: How to Determine Which Public Folder Replica is Used
	
	Additional query words: sub-site sub site connection modulus sort order subsite subsites
	
	======================================================================
	Keywords          : exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : :5.0,5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
