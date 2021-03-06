---
layout: page
title: "Q300626: FIX: Unable to Specify Folder Path for Moderated Newsgroups"
permalink: /kb/300/Q300626/
---

## Q300626: FIX: Unable to Specify Folder Path for Moderated Newsgroups

{% raw %}

	Article: Q300626
	Product(s): Internet Information Server
	Version(s): 2.0,2.5,4.0,5.0
	Operating System(s): 
	Keyword(s): tslic_tslic
	Last Modified: 08-MAY-2002
	
	IMPORTANT: This article contains information about editing the metabase. Before you edit the metabase, verify that you have a backup copy that can be restored if a problem occurs. For information about how to do this, view the "Configuration Backup/Restore" Help topic in Microsoft Management Console (MMC).
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 4.0, 5.0 
	- Microsoft Commercial Internet System versions 2.0, 2.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to specify a folder path for a moderated newsgroup under the
	Network News Transfer Protocol (NNTP) virtual server settings, you may receive
	the following error message:
	
	  The domain name is not valid.
	
	CAUSE
	=====
	
	The Internet Information Services (IIS) Help documentation states that you can
	either specify a Simple Mail Transfer Protocol (SMTP) server name or a folder
	path for moderated newsgroups. The IIS Management Console only allows
	alphanumeric characters and a period (.) to specify a valid server name or fully
	qualified domain name (FQDN).
	
	RESOLUTION
	==========
	
	WARNING: Editing the metabase incorrectly can cause serious problems that may
	require you to reinstall any product that uses the metabase. Microsoft cannot
	guarantee that problems resulting from incorrectly editing the metabase can be
	solved. Edit the metabase at your own risk.
	
	NOTE: You should always back up the metabase before you edit it.
	
	To work around this problem, specify the folder path as a value to the SMTP
	virtual server metabase key. To do this, follow these steps:
	
	1. Locate the Adsutil.vbs script file that is installed by IIS. You will use
	  this file to modify the metabase.
	
	2. Specify the folder path name for moderated newsgroups. The syntax is as
	  follows:
	
	  cscript adsutil.vbs set nntpsvc/<virtual server instance id>/smtpserver "<path>"
	
	For example, if you want to specify the path as C:\Moderated for the default NNTP
	server instance, run the following from a command prompt:
	
	  cscript adsutil.vbs set nntpsvc/1/smtpserver "c:\moderated"
	
	3. After the setting is applied, you can either restart all of the IIS services
	  or restart the server.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	The problem occurs on a new installation of an NNTP server, where no moderated
	path has been specified and does not exist for the nntpsvc/1/smtpserver key in
	the metabase. You must have the Web server, SMTP server, and NNTP services
	installed from the Microsoft Windows 2000 or Microsoft Windows NT Option Pack,
	or equivalent services from Microsoft Commercial Internet System (MCIS) version
	2.0.
	
	1. Start the Internet Service Manager (ISM), which loads the IIS snap-in for the
	  Microsoft Management Console (MMC).
	
	2. Right-click Default NNTP Virtual Server and click Properties.
	
	3. Click the Settings tab.
	
	4. Under SMTP server for moderated groups type a valid folder path (for example,
	  C:\Inetpub or \Inetpub) and click either Apply or OK.
	
	Additional query words: Windows NT4, Option Pack 4, MCIS 2.0, SMTP, NNTP, IIS
	
	======================================================================
	Keywords          : tslic_tslic 
	Technology        : kbiisSearch kbAudDeveloper kbiis500 kbiis400 kbMCISSearch kbMCIS200 kbMCIS250
	Version           : :2.0,2.5,4.0,5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
