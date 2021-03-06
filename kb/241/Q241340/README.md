---
layout: page
title: "Q241340: Branch Office Scenario Selects All SNA Subcomponents"
permalink: /kb/241/Q241340/
---

## Q241340: Branch Office Scenario Selects All SNA Subcomponents

{% raw %}

	Article: Q241340
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.5
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 01-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft BackOffice Server 4.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you perform a Branch Office scenario installation of BackOffice Server 4.5,
	all the Microsoft SNA Server subcomponents are selected. This causes all of the
	SNA Server 4.0 SP2 components to be installed, requiring approximately 130.3
	megabytes (MB) of disk space.
	
	CAUSE
	=====
	
	The Intranet Publishing Server, Intranet Collaboration Server, and Complete
	installation scenarios present the following prompt:
	
	  Does this server access information on an AS/400 or a mainframe computer?
	
	If you click Yes, SNA Server 4.0 SP2 becomes one of the programs that is
	installed. However, for these three scenarios, not all of the SNA Server
	subcomponents are installed. The SNA Server components installed are the same
	for all three scenarios. The components that are not installed include:
	
	- Under SNA Server 4.0 SP2:
	
	   - Online Help (9.2 MB)
	
	- Under "SNA Server Component and Services":
	
	   - Host Account Synchronization Service (0.3 MB)
	   - SNA Remote Access Server (0.4 MB)
	
	- Under "Applications and Development Tools":
	
	   - COM Transaction Integrator (12.7 MB)
	   - OLE DB Provider for AS400 and VSM (4.6 MB)
	
	The Branch Office scenario does not present the prompt because it assumes that
	the answer is "yes," and all of the SNA Server 4.0 SP2 components are selected
	for installation.
	
	RESOLUTION
	==========
	
	Use the following method during a Branch Office scenario installation process if
	you do not want all the selected components to be installed:
	
	1. In the Your BackOffice Branch Office Server Installation dialog box, click
	  Customize My Solution.
	
	2. Go to the SNA Server 4.0 SP2 component.
	
	3. Follow the tree, and click to clear the check boxes for the components you do
	  not want to install.
	
	4. When you are finished with the selection process, click Next.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsetup 
	Component         : Component SRVRSetup
	Technology        : kbAudDeveloper kbBackOfficeSearch kbBackOfficeServ450
	Version           : winnt:4.5
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
