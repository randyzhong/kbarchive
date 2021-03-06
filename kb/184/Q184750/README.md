---
layout: page
title: "Q184750: Err Msg: Unable to Load the Remote Access Library..."
permalink: /kb/184/Q184750/
---

## Q184750: Err Msg: Unable to Load the Remote Access Library...

{% raw %}

	Article: Q184750
	Product(s): The Microsoft Network
	Version(s): WINDOWS:1.3,2.0,2.5,2.51,2.52,2.6
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbmsn
	Last Modified: 22-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network versions 1.3, 2.0, 2.5, 2.51, 2.52, 2.6 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to connect to the Microsoft Network, you may receive the following
	error message:
	
	  Unable to load the Remote Access Library (Rasapi32.dll). The following error
	  occurred: The system could not find the file specified.
	
	CAUSE
	=====
	
	This behavior can occur if the Rasapi32.dll file is missing or damaged.
	
	RESOLUTION
	==========
	
	To resolve this issue, extract a new copy of the Rasapi32.dll file from your
	original Windows 95 CD-ROM or disks to the Windows\System folder.
	
	The Rasapi32.dll file is located in the following places:
	
	  Windows 95 CD-ROM: Win95_10.cab cabinet file
	  Windows 95 OEM Service Release 2 CD-ROM: in the Win95_16.cab cabinet file
	  Windows 95 DMF format disks (disk 10): in the Win95_10.cab cabinet file
	  Windows 95 non-DMF format disksand (disk 16): in the Win95_16.cab cabinet
	  file
	  Windows 98 CD-ROM: Win98_37.cab cabinet file
	
	NOTE: If you are prompted to overwrite an existing file, click Yes, and then
	press ENTER.
	
	For information about using the Extract tool, type extract at a command prompt,
	or see the following article in the Microsoft Knowledge Base:
	
	  Q129605 <A0>How to Extract Original Compressed Windows Files
	
	This behavior can also occur if the Internet Connection Wizard is damaged in
	Windows 95.
	
	To resolve this issue, reinstall the Internet Connection Wizard. To do this,
	follow these steps:
	
	1. Connect to MSN using Dial-Up Networking.
	
	For information about how to connect to MSN using Dial-Up Networking, please see
	the following article in the Microsoft Knowledge Base: 173587 How to Connect to
	the Internet Using MSN"/>
	2. Double-click the Internet Explorer icon on the desktop.
	
	3. On the Help menu, click Product Updates.
	
	4. If you are prompted to download an updated version of Internet Explorer,
	  click Yes. Follow the instructions on the screen to download and install
	  Internet Explorer 4.01 Service Pack 1 (SP1). If Active Setup prompts you to
	  determine what Internet components are installed on your computer, skip to
	  the If Internet Explorer 4.01 SP1 is already installed on your computer
	  section later in this article.
	
	5. When the installation is complete, disconnect from MSN and then restart the
	  computer.
	
	If Internet Explorer 4.01 SP1 Is Already Installed on Your Computer
	
	If Internet Explorer 4.01 SP1 is already installed on your computer, follow these
	steps:
	
	1. When Active Setup prompts you to determine what Internet components are
	  installed on your computer, click Yes.
	
	2. Click the Internet Connection Wizard check box. When you are prompted to
	  reinstall this component, click Yes, and then click Next.
	
	3. Click a download site, and then click Install Now.
	
	4. When the installation is complete, disconnect from MSN and then restart the
	  computer.
	
	Additional query words: msnetwork microsoft-net m.s.n. dun win95x win98x rasapi32 dll
	
	======================================================================
	Keywords          : kbenv kberrmsg kbmsn 
	Technology        : kbMSNSearch kbMSN200 kbMSN252 kbMSN130 kbMSN251 kbMSN260 kbMSN250
	Version           : WINDOWS:1.3,2.0,2.5,2.51,2.52,2.6
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
