---
layout: page
title: "Q150227: BUG: Control Loses Focus When Another Window is Activated"
permalink: /kb/150/Q150227/
---

## Q150227: BUG: Control Loses Focus When Another Window is Activated

{% raw %}

	Article: Q150227
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If the TabStop property of a control is set to False and the focus is set to
	that control at run-time, and if another window in the same application or a
	different application is activated, when the focus is set back to the original
	window, the control no longer has the focus.
	
	RESOLUTION
	==========
	
	Temporarily set the TabStop property to True in the GotFocus event, and set it
	back to False in the LostFocus event. If the user changes over to another
	application or window while the control has the focus, the focus returns to the
	original control when the window is activated. For example, if, at the beginning
	of the program, the Text1 control was not going to have the focus, the following
	code could be inserted in the GotFocus and LostFocus events of the Text
	control:
	
	     Private Sub Text1_GotFocus()
	        Text1.TabStop = True
	        End Sub
	        Private Sub Text1_LostFocus()
	        Text1.TabStop = False
	     End Sub
	
	STATUS
	======
	
	Microsoft has confirmed this to be an issue in the Microsoft products listed at
	the beginning of this article. Microsoft is researching this issue and will post
	new information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start a new project in Visual Basic. Form1 is created by default.
	
	2. Place two Text boxes on Form1.
	
	3. Set the TabStop property of the Text1 text box to False.
	
	4. Run the project by pressing F5. Note that the Text2 text box has the focus
	  when the form appears. Click on the Text1 text box, and then click on any
	  other window in the Desktop, or press ALT+TAB to switch to another
	  application.
	
	5. Return the focus to Form1 by clicking on its Title bar or by pressing
	  ALT+TAB. Note that the Text2 text box has the focus.
	
	To work around this problem, place the code in the Workaround Section above into
	the code for Form1.
	
	Additional query words: kbVBp400bug kbVBp500bug kbVBp600bug kbVBp kbdsd kbDSupport kbControl
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbZNotKeyword3 kbVB16bitSearch
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
