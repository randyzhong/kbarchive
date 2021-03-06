---
layout: page
title: "Q325608: PRB: Authentication Delegation Through Kerberos Does Not Work"
permalink: /kb/325/Q325608/
---

## Q325608: PRB: Authentication Delegation Through Kerberos Does Not Work

{% raw %}

	Article: Q325608
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a customer tries to use Kerberos to delegate authentication in a
	load-balanced architecture, Kerberos does not work and Internet Information
	Services (IIS) drops back to Windows NT Challenge/Response authentication.
	Because Windows NT Challenge/Response cannot be used for delegation, any
	applications or services that require delegation do not work.
	
	CAUSE
	=====
	
	The problem occurs because of a limitation in the Kerberos authentication
	protocol. The load-balanced cluster uses a virtual host name to identify itself,
	and this is the host name that the Kerberos ticket is issued for. When the
	ticket is presented to the actual server, the client that is directed to the
	ticket does not match its Server Principal Name (SPN). Additionally, in a
	Windows 2000 domain, the virtual host name cannot be set to Trusted For
	Delegation in the Active Directory.
	
	When the server rejects the Kerberos ticket, the client renegotiates and tries to
	use Windows NT Challenge/Response authentication. Even if the client can
	authenticate through this method, delegation fails because it relies on Kerberos
	to function.
	
	WORKAROUND
	==========
	
	One possible workaround requires that each computer in the load-balanced cluster
	be available to answer to its own fully qualified domain name (FQDN). The
	default page on each server must redirect the client directly to itself, thereby
	bypassing the virtual host name and instead providing a valid host name that a
	ticket can be issued for.
	
	As a sample, the page can be something a simple as the following line:
	
	  <% response.redirect("http://my.unique.fqdn/default2.asp") %>
	
	Assuming that my.unique.fqdn is the unique FQDN of the computer and that
	Default2.asp is the actual default page that the client must be directed to,
	Kerberos can use this simple redirection to work in a load-balanced
	architecture.
	
	As a caveat, the client can see or record (that is, bookmark) the unique name of
	the server that the client is directed to. This may seem to lead to outages if
	the client bookmarks that site and tries to return when either the physical
	server or the unique server name is unavailable.
	
	MORE INFORMATION
	================
	
	For more information about the Kerberos authentication protocol, see the
	following RFC Web site:
	
	  RFC 1510
	  http://www.ietf.org/rfc/rfc1510.txt
	
	Additional query words: iis 5 wlbs kerberos delegation integrated
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
