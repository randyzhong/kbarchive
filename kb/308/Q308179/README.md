---
layout: page
title: "Q308179: BUG: Virtual Directories Disappear from the IIS 5.1 Snap-in"
permalink: /kb/308/Q308179/
---

## Q308179: BUG: Virtual Directories Disappear from the IIS 5.1 Snap-in

{% raw %}

	Article: Q308179
	Product(s): Internet Information Server
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 31-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.1, used with:
	   - the operating system: Microsoft Windows XP 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a new virtual directory is created under a physical Web directory in the
	Internet Information Services (IIS) snap-in, the virtual directory may disappear
	when you refresh the tree list view.
	
	NOTE: The _vti_bin virtual directory of a newly created FrontPage Server
	Extensions (FPSE) subweb also disappears from the IIS snap-in when you refresh
	the tree list view.
	
	CAUSE
	=====
	
	A logic problem in the IIS snap-in code allows creation of IIsVirtualDir nodes
	underneath IIsWebDirectory nodes in the IIS metabase, but then fails to
	enumerate the IIsWebVirtualDir nodes after the nodes are created.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	Perform the following steps on a computer with Windows XP Professional and
	Internet Information Services 5.1 installed.
	
	NOTE: These steps use the FrontPage Server Extensions to create a physical Web
	directory. This issue is not a problem with the FrontPage Server Extensions;
	however, these steps highlight the most common scenario in which the issue
	manifests itself.
	
	1. Open the IIS snap-in. To do this, click Start, click Programs, click
	  Administrative Tools, and then click Internet Information Services.
	
	2. Expand the (local computer) and Web Sites nodes.
	
	3. Right-click Default Web Site, click New, and then select Server Extensions
	  Web.
	
	4. Complete the New Subweb Wizard. Type valid names for the subweb directory
	  name and title.
	
	Note that the _vti_bin virtual directory is missing.
	
	5. Expand the subweb node that you just created.
	
	6. Right-click the Images folder, click New, and then click Virtual Directory.
	
	7. Complete the Virtual Directory Creation Wizard. Type a valid name for the
	  virtual directory and configure the path as a valid directory on the
	  computer.
	
	The new virtual directory appears in the tree list view under the Images folder.
	
	8. Right-click the Default Web Site node and click Refresh.
	
	The virtual directory that you just created disappears from the tree list.
	
	
	Additional query words: vdir virtual directory disappears mmc iis 5.1 fpse _vti_bin
	
	======================================================================
	Keywords          :  
	Technology        : kbWinXPPro kbiisSearch kbWinXPProSearch kbWinXPSearch kbiis510
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
