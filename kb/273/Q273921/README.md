---
layout: page
title: "Q273921: Crimson Skies: &quot;Abnormal Program Termination&quot; Error Message"
permalink: /kb/273/Q273921/
---

## Q273921: Crimson Skies: &quot;Abnormal Program Termination&quot; Error Message

{% raw %}

	Article: Q273921
	Product(s): Microsoft Home Games
	Version(s): 
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbimu msgame
	Last Modified: 22-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Crimson Skies 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you turn a page in the Scrapbook in Microsoft Crimson Skies after you
	finish several missions in which you flew through all of the danger zones, you
	may receive the following error message:
	
	  Microsoft Visual C++ Runtime Library
	  Runtime Error!
	  Program... \CRIMSON.ICD
	  Abnormal program termination.
	
	When you click OK, the program quits.
	
	CAUSE
	=====
	
	This behavior can occur if your computer runs out of available hard disk space
	for virtual memory.
	
	RESOLUTION
	==========
	
	To prevent this issue from occurring, increase the amount of available memory or
	hard disk space in your computer. To do this, use one or more of the following
	methods.
	
	Quit Unnecessary Programs
	-------------------------
	
	Quit any unnecessary programs that are running on your computer before you start
	Crimson Skies. To do this:
	
	1. Disable any anti-virus programs or disk utilities that are installed on the
	  computer. For information about how to disable these programs, see the
	  printed or online documentation for the program.
	
	2. Press CTRL+ALT+DELETE to open the Close Program dialog box.
	
	3. In the Close Program dialog box, click any program except Explorer or Systray
	  (which are components of Microsoft Windows) or Netscape Navigator, and then
	  click End Task.
	
	  If you receive a message stating that the program is busy or not responding,
	  click End Task again.
	
	4. Repeat steps 2 and 3 to quit all unnecessary programs.
	
	If the issue continues to occur, proceed to the next method.
	
	Make Sure That Virtual Memory Is Enabled on Your Computer
	---------------------------------------------------------
	
	Make sure that virtual memory is enabled on your computer. To do this:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. Click the Performance tab.
	
	4. Click Virtual Memory.
	
	5. Make sure that the "Disable virtual memory. (Not recommended)" check box is
	  cleared.
	
	6. Click "Let Windows manage my virtual memory settings. (Recommended)", and
	  then click OK.
	
	7. If you are prompted to restart the computer, do so.
	
	If the issue continues to occur, proceed to the next method.
	
	Increase the Amount of Available Hard Disk Space
	------------------------------------------------
	
	To increase the amount of available hard disk space in your computer:
	
	1. Right-click the Recycle Bin icon on the desktop, click Empty Recycle Bin, and
	  then click Yes.
	
	2. Back up and then remove any files on the hard disk that you do not use
	  frequently.
	
	  For information about how to back up your files, click Start, and then click
	  Help. On the Index tab, type "backing" (without the quotation marks), and
	  then double-click the "Backing up files" or "Backing up files, folders"
	  topic.
	
	3. Delete any unnecessary files on the hard disk.
	
	  For information about how to delete files, click Start, and then click Help.
	  On the Index tab, type "deleting" (without the quotation marks), and then
	  double-click the "Deleting files or folders" or "Deleting files, folders"
	  topic.
	
	If the issue continues to occur, you may need to install additional memory in
	your computer.
	
	To determine the amount of memory that is installed in your computer:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. On the General tab, note the amount of memory that is displayed under
	  Computer, and then click OK.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Crimson Skies.
	
	MORE INFORMATION
	================
	
	You may also be able to work around this issue by quitting and restarting the
	game after you complete several missions.
	
	Additional query words: 1.00 msgame crimskies cs cskies
	
	======================================================================
	Keywords          : kbenv kberrmsg kbimu msgame 
	Technology        : kbHomeProdSearch kbGamesSearch kbCrimsonSkiesSearch
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
