---
layout: page
title: "Q186270: BUG: SSTab Control Containing OLE Control May Crash"
permalink: /kb/186/Q186270/
---

## Q186270: BUG: SSTab Control Containing OLE Control May Crash

{% raw %}

	Article: Q186270
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0,97,97sp2,97sp3
	Operating System(s): 
	Keyword(s): kbusage kbCtrl kbVBp kbVBp500bug kbVBp600bug kbVS97 kbVS97sp2 kbVS97sp3 kbGrpDSVB kbDSu
	Last Modified: 13-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Studio versions 97, 97sp2, 97sp3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On a Visual Basic form, an OLE control is placed on a Microsoft Tabbed Dialog
	control. You write code to embed a file into the OLE control using the
	CreateEmbed method. When the user clicks the tab that contains the OLE control,
	one of the following errors occur and the application terminates:
	
	  VB5 caused an invalid page fault in module TABCTL32.OCX at 0137:212f8b26.
	
	-or-
	
	  <Project Name> executed an invalid instruction in module OLE32.DLL at
	  0137:65fa93ae.
	
	-or-
	
	  Exception: Access violation (0xc0000005), Address: 0x212f8b26
	
	RESOLUTION
	==========
	
	To work around this problem, do one of the following:
	
	- Place the OLE control inside a Frame control.
	
	  -or-
	
	- Make the Tab that contains the OLE control the active tab before using the
	  CreateEmbed method.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new Standard EXE project. Form1 is created by default. Choose
	  Components from the Project menu and add a reference to the "Microsoft Tabbed
	  Dialog Control 5.0."
	
	2. Add an SSTab control to Form1. By default, there will be three tabs named
	  Tab0, Tab1 and Tab2. Add a CommandButton to Form1.
	
	3. Add an OLE control to the first tab, Tab0, of the SSTab control. Choose
	  Cancel when prompted to insert an object.
	
	4. Paste the following code into the code window of Form1:
	
	        Private Sub Command1_Click()
	          'Set the current tab to the second tab
	          SSTab1.Tab = 1
	
	          'Embed a bitmap into the OLE control
	          OLE1.CreateEmbed "C:\VB5\Graphics\Bitmaps\Assorted\Envelope.bmp"
	        End Sub
	
	5. Change the path in the code above to a valid BMP file on your system.
	
	6. Save and run the project.
	
	7. Click Command1. Click Tab0 and note that the OLE control displays the bitmap
	  file.
	
	8. Click Command1 and then click Tab0.
	
	Note that Visual Basic terminates with one of the errors mentioned above. If no
	problem occurs, repeat steps 7 and 8. If the problem still does not occur, try
	restarting Visual Basic and repeat the steps beginning at step 6. This problem
	also occurs when running the project as a compiled .exe file.
	
	Workaround
	----------
	
	To work around this problem, put a Frame control on Tab0 and then put the OLE
	control inside the Frame control. Size the Frame control so it is large enough
	to accommodate the OLE control and set the Borderstyle property of the Frame
	control to 0 if you wish to hide the Frame's border and caption.
	
	Additional query words: ipf OLE container
	
	======================================================================
	Keywords          : kbusage kbCtrl kbVBp kbVBp500bug kbVBp600bug kbVS97 kbVS97sp2 kbVS97sp3 kbGrpDSVB kbDSupport 
	Technology        : kbVSsearch kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600 kbVS97 kbVS97SP2 kbVS97SP3 kbVS97Search
	Version           : WINDOWS:5.0,6.0,97,97sp2,97sp3
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
