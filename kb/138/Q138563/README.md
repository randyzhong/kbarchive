---
layout: page
title: "Q138563: FIX: Form Not Cleared from Memory When Grid Has the Focus"
permalink: /kb/138/Q138563/
---

## Q138563: FIX: Form Not Cleared from Memory When Grid Has the Focus

{% raw %}

	Article: Q138563
	Product(s): Microsoft FoxPro
	Version(s): 3.00 3.00b
	Operating System(s): 
	Keyword(s): kbvfp kbvfp300bBUG kbvfp500fixkbbuglist kbfixlist
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The RELEASE command will not release a form from memory if a grid has the focus
	when the form is released. The form is cleared off the screen, but
	_screen.formcount is not decremented, and _screen.activeform.name still shows
	the name of the form in the Debug window. If another object on the form, such as
	a text box, has the focus when the form is released, _screen.formcount is
	decremented, and _screen.activeform.name is cleared.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem has been fixed in Visual FoxPro 5.0
	for Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Create s program named Main.prg that contains this code:
	
	     SET PROCEDURE TO Main.prg
	     ON KEY LABEL F12 CLEAR EVENTS
	     ON KEY LABEL F11 SET SYSMENU TO DEFAULT
	
	     DO MyMenu.MPR
	     READ EVENTS
	
	     SET SYSMENU TO DEFAULT
	
	     PROCEDURE ClearForms                  && Clear all open forms
	         IF _SCREEN.FormCount > 0
	              FOR i = _SCREEN.FormCount TO 1 STEP -1
	                   _SCREEN.Forms(i).Release
	              ENDFOR
	         ENDIF
	
	2. Create a menu named MyMenu.
	
	  a. Add a Form1 prompt that uses this command:
	
	        DO FORM Form1.SCX
	
	  b. Add a Clear Forms prompt that uses this command:
	
	        DO ClearForms
	
	  c. Add an Exit program prompt that uses this command:
	
	        CLEAR EVENTS
	
	  d. Generate and save the menu in the directory where Main.prg is located.
	
	3. Create a form named Form1.
	
	  a. Add the Customer and Orders tables located in the Vfp\Samples\Data
	     directory to the data environment.
	
	  b. Drag a field from the Customer table onto the form to create a text box.
	
	  c. Drag the Orders table onto the form to create a grid.
	
	  d. Save the form in the directory where Main.prg is located.
	
	4. Open the Debug window and place _screen.formcount in the left pane.
	
	5. Run Main.prg.
	
	6. Click the Form1 menu, and then click the grid to give it the focus.
	  _screen.formcount will equal 1. Multiple instances of Form1 can be run with
	  the same result.
	
	7. Release Form1 by clicking the Clear Forms menu. Form1 will clear off the
	  screen, but _screen.formcount will still equal 1.
	
	8. Exit the program, or click the Clear Forms menu again to return
	  _screen.formcount to 0.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp kbvfp300bBUG kbvfp500fix kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b
	Version           : 3.00 3.00b
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
