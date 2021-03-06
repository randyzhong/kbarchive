---
layout: page
title: "Q168055: PRB: Files Saved to Novell Server May Give Read-Only Message"
permalink: /kb/168/Q168055/
---

## Q168055: PRB: Files Saved to Novell Server May Give Read-Only Message

{% raw %}

	Article: Q168055
	Product(s): Microsoft FoxPro
	Version(s): 5.0a,6.0,7.0
	Operating System(s): 
	Keyword(s): kbinterop kbnetwork kbvfp kbvfp500a kbvfp600
	Last Modified: 28-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0a, 6.0, 7.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When saving a form or a menu to a Novell server from a Windows NT 4.0 computer
	running Novell IntranetWare Client 4.1, an erroneous message may occur:
	
	  "File ... is read-only."
	
	MORE INFORMATION
	================
	
	IntranetWare 4.1 is the 32-bit client for Windows NT computers. The behavior is
	usually seen using this client on Windows NT 4.0 computers. The behavior has not
	been observed on a Windows NT 3.51 computer (with Service Pack 5).
	
	The problem appears to occur mainly when saving writeable Form or Menu files that
	are within a project, although the behavior has also been observed with
	stand-alone files. In some cases, the behavior is more evident on Windows NT 4.0
	computers that have Service Pack 2 or Service Pack 4 installed.
	
	The problem appears to be intermittent when saving forms but occurs most when
	saving menus a second time. Other file types may exhibit the same behavior.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. On a Windows NT 4.0 computer with Service Pack 2 installed using the Novell
	  IntranetWare 4.1 client, create a project on the Novell server.
	
	2. In the project, create a menu that has a Result of "Submenu" but which has no
	  submenu, and save it.
	
	3. Modify the menu and attempt to save it. The error should occur when
	  attempting to save the menu.
	
	NOTE: The behavior does not occur when "Command" is selected as the menu item
	result and a valid command is entered. The ReadOnly dialog appears
	intermittently when saving forms.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbinterop kbnetwork kbvfp kbvfp500a kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600 kbVFP700 kbVFP500a
	Version           : :5.0a,6.0,7.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
