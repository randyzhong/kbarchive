---
layout: page
title: "Q130725: How to Use the CloneObject Method"
permalink: /kb/130/Q130725/
---

## Q130725: How to Use the CloneObject Method

{% raw %}

	Article: Q130725
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 11-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can use the CLONEOBJECT() method to duplicate an object on the Form Designer
	at form-design time. If you are developing a wizard or builder, you can use
	CLONEOBJECT to add an object to a form. This article provides an example that
	illustrates how to use this method.
	
	MORE INFORMATION
	================
	
	Step-by-Step Example
	--------------------
	
	This example runs a modal form that determines the number of controls to be
	placed on a form. This modal dialog box returns a value to the program. In this
	code, a command button is created, and the CLONEOBJECT method duplicates the
	command button. Note that the caption for each of the buttons is blue.
	
	1. Create a form. Using the following table as a guide, modify the form's
	  properties and methods. Name the form CLONEOBJ.
	
	  Property       What to Type in the Property Sheet
	  ------------------------------------------------------------------------
	  BackColor      192,192,192
	  Caption        Enter Number of Controls
	  Unload Event   RETURN nValue        &&This is the value the form returns
	  WindowType     1-Modal
	
	2. Place a spinner on the form. Using the following table as a guide, modify the
	  spinner's properties:
	
	  Property          Type in the Property Sheet
	  ------------------------------------------------------------------------
	  ControlSource     nValue
	  KeyboardHighvalue 10
	  KeyboardLowValue   1
	  SpinnerHighValue  10
	  SpinnerLowValue    1
	
	3. Place a command button on the form. Using the following table as a guide,
	  modify the command button's properties:
	
	  Property          Type in the Property Sheet
	  ------------------------------------------------------------------------
	  Caption           OK
	  Click Event       RELEASE ThisForm
	
	4. Copy and paste the following code into a program file (.PRG file), and run
	  it.
	
	        *:   CLONEOBJ
	        DO Form CloneObj TO nNumberofControls
	
	        CREATE Form test2 NOWAIT
	
	        =ASELOBJ(atest,1)       && Place the name of the form in an array.
	        atest(1).Caption="See the new controls on the Form"
	        atest(1).LockScreen=.T. && Changes are refreshed all at once
	        =MESSAGEBOX('There is no control')
	
	        * Define the first command button:
	        atest(1).AddObject('mycmd1','CommandButton')
	        atest(1).mycmd1.ForeColor=RGB(0,0,255)
	
	        * Duplicate the first command button, and store the name of the
	        * previous command button to position the new control relative to the
	        * position of the previous command button:
	        FOR I=2 TO nNumberofControls
	           OldName='Mycmd'+ALLTRIM(STR(I-1))
	           NewName='Mycmd'+ALLTRIM(STR(I))
	
	           atest(1).mycmd1.CloneObject(NewName) && Duplicate command button.
	           oref=EVALUATE('atest(1).'+NewName)
	           oOldref=EVALUATE('atest(1).'+OldName)
	           oref.Top=oOldref.Top+35
	           oref.Caption=NewName
	
	        ENDFOR
	        atest(1).SetAll('Visible',.T.,'CommandButton')
	        atest(1).Refresh
	        =MESSAGEBOX('Now there are '+ ALLTRIM(STR(nNumberofControls))+ ;
	        ' controls')
	
	The above program creates a form called TEST2.SCX with the number of command
	buttons specified in the first form's spinner. When the program file finishes
	running, TEST2.SCX remains open for modifications.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
