---
layout: page
title: "Q257783: FIX: Function with Numeric Label May Cause Crash"
permalink: /kb/257/Q257783/
---

## Q257783: FIX: Function with Numeric Label May Cause Crash

{% raw %}

	Article: Q257783
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbVBp kbVBp600bug kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you have a line of code that calls a function which returns a double data
	type and that line of code is followed by a line of code with a numeric label,
	you receive an Access Violation when you try to build the executable file.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article. This bug was corrected in the latest
	service pack for Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the following
	article numbers to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	To download the latest Visual Studio service pack, visit the following Microsoft
	Web site:
	
	  http://msdn.microsoft.com/vstudio/downloads/updates.asp
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new ActiveX EXE project. Class1 is added by default.
	
	2. Paste the following code into the code window of Class1:
	
	  Option Explicit
	
	  Public Sub Test()
	    Debug.Assert (CDbl(Now) = 1.1)
	  10:     MsgBox "Hey"
	  End Sub
	
	3. Save the project.
	
	4. From the File menu, choose Make Project1.exe, and note that an Access
	  Violation error occurs.
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbVBp kbVBp600bug kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
