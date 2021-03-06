---
layout: page
title: "Q267999: FIX: FrontPage 98 and VisID Cannot Open Web Through SSL"
permalink: /kb/267/Q267999/
---

## Q267999: FIX: FrontPage 98 and VisID Cannot Open Web Through SSL

{% raw %}

	Article: Q267999
	Product(s): Internet Information Server
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbOSWin2000 kbiis500prod2web kbProd2Web
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Information Server version 4.0 
	- Microsoft FrontPage 98 for Windows 
	- Microsoft FrontPage 97 for Windows 
	- Microsoft Visual InterDev, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use Internet Information Services (IIS) 5.0 or Internet Information
	Server (IIS) 4.0 with the FrontPage Server Extensions and with a Verisign or
	Rivest-Shamir-Adleman (RSA) certificate, attempting to open Web sites in the
	FrontPage 98 client or Visual InterDev through HTTPS may fail. The root
	certificate authority is not recognized as a trusted authority, and therefore,
	the connection is not allowed. However, if the Web site is viewed in a browser,
	such as Internet Explorer 4.01 SP1 or later, you can view the Web site without
	problems.
	
	CAUSE
	=====
	
	The FrontPage 98 client and Visual InterDev only support a few select
	Certificate Authorities. The FrontPage 98 client and Visual InterDev only
	support 40-bit encryption. Verisign has changed their original 40-bit
	certificate, which causes FrontPage 98 and Visual InterDev to not recognize the
	Root CA as a trusted authority.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  
	
	  File Name    Size     Date       Time     Version     Platform
	  --------------------------------------------------------------
	  Fp30wec.dll  413,968  12/6/2000  3:22 PM  3.0.2.4806  x86
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	For another way to resolve this issue, follow these steps:
	
	1. Create a new certificate request on the IIS 4.0 or 5.0 server.
	
	2. Submit the request to Verisign, and make sure that "IBM" is selected as the
	  server type, as opposed to "Microsoft" (contact Verisign for help obtaining
	  this certificate).
	
	3. Make sure that the previous certificate has been removed from the Key
	  Manager, and make sure to "Commit All Changes" afterwards.
	
	4. When the new certificate has been received from Verisign, install the
	  certificate to the appropriate Web site.
	
	5. In a browser, test HTTPS access. In FrontPage 98 or Visual InterDev, test
	  HTTPS access again.
	
	This resolution should provide access to the Web site from FrontPage 98 and
	Visual InterDev through HTTPS.
	
	REFERENCES
	==========
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q238662 INFO: Using Visual InterDev and Secure Sockets Layer
	
	  Q194672 FP98: "Socket Code 4" Error Connecting to Server Using SSL
	
	Additional query words: SSL
	
	======================================================================
	Keywords          : kbOSWin2000 kbiis500prod2web kbProd2Web 
	Technology        : kbVisIDsearch kbiisSearch kbFrontPageSearch kbAudDeveloper kbFrontPage97 kbiis500 kbiis400 _IKkbZNotKeyword4 kbZNotKeyword2 kbFrontPage97Search kbFrontPage98Search kbZNotKeyword3 kbVisID600
	Version           : :4.0,5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
