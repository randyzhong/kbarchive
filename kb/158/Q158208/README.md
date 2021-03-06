---
layout: page
title: "Q158208: FIX: Form with Toolbar Does Not Shut Down Under Windows NT 4.0"
permalink: /kb/158/Q158208/
---

## Q158208: FIX: Form with Toolbar Does Not Shut Down Under Windows NT 4.0

{% raw %}

	Article: Q158208
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0; winnt:4.0
	Operating System(s): 
	Keyword(s): kbnokeyword kbVBp kbVBp400bug kbVBp500fix kbGrpDSVB kbDSupport
	Last Modified: 04-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Enterprise Edition for Windows, version 4.0, on platform(s):
	   - the hardware: Intel x86 
	- the operating system: Microsoft Windows NT 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Visual Basic 4.0 program containing a standard Visual Basic 4.0 Toolbar
	control on a form and running on Windows NT 4.0 hangs during Windows NT shut
	down.
	
	The following message is displayed when you attempt to shut down Windows NT while
	your application containing the Toolbar control is still running:
	
	  The Windows application cannot respond to the End Task request. It may be
	  busy, waiting for a response from you, or it may have stopped executing.
	
	  - Press Cancel to cancel and return to Windows NT.
	
	  - Press End Task to close this application immediately. You will lose any
	  unsaved information in this application.
	
	  - Press Wait to give application 20 seconds to finish what it is doing and
	  then try to close the application again.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Basic 5.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start 32-bit Visual Basic 4.0 or, if it is already running, click New Project
	  on the File menu.
	
	2. Add a Toolbar control to Form1.
	
	3. On the File menu, click Make EXE to make an executable file out of your
	  project. Close Visual Basic.
	
	4. Start the executable file created in the previous step. On the Windows Start
	  button, click Shutdown, and then click Restart. After a few seconds, the
	  following message appears:
	
	  The Windows application cannot respond to the End Task request. It may be
	  busy, waiting for a response from you, or it may have stopped executing.
	
	  - Press Cancel to cancel and return to Windows NT.
	
	  - Press End Task to close this application immediately. You will lose any
	  unsaved information in this application.
	
	  - Press Wait to give application 20 seconds to finish what it is doing and
	  then try to close the application again.
	
	  Click Cancel to close the message.
	
	5. Click the Close button to close the Visual Basic program.
	
	Additional query words: Toolbar
	
	======================================================================
	Keywords          : kbnokeyword kbVBp kbVBp400bug kbVBp500fix kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2
	Version           : WINDOWS:4.0; winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
