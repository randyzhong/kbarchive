---
layout: page
title: "Q150206: BUG: DBGrid on a Modal Form Can Cause a Program to Hang"
permalink: /kb/150/Q150206/
---

## Q150206: BUG: DBGrid on a Modal Form Can Cause a Program to Hang

{% raw %}

	Article: Q150206
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.00
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A program hangs if a DBGrid control is placed on a Modal Form, which itself was
	invoked from a Modal form from an MDIChild window, and the form containing the
	DBGrid is then closed. Usually the window receiving the focus after the form
	with the DBGrid control is closed begins to flash, and does not respond to user
	input.
	
	STATUS
	======
	
	Microsoft has confirmed this to be an issue in the Microsoft products listed at
	the beginning of this article. Microsoft is researching this issue and will post
	new information here in the Microsoft Knowledge Base as it becomes available.
	
	WORKAROUND
	==========
	
	Show the form containing the DBGrid in a non-modal fashion, and disable the
	other forms in the project until the non-modal form is dismissed. The routine
	below shows a form that appears as a modal form:
	
	     Public Sub ShowModalForm(frmTarget As Form)
	
	     Dim c As Collection
	     Set c = New Collection
	
	     'Disable all the forms
	     For Each ofrm In Forms
	         If ofrm.Enabled = True Then
	         c.Add ofrm
	         ofrm.Enabled = False
	         End If
	
	     Next ofrm
	
	     'Now show the target form non-modal
	     frmTarget.Show
	
	     'If the frmTarget was disabled by the loop above
	     '(because it was invisible) make sure it is now enabled
	
	     frmTarget.Enabled = True
	
	     'Sit in a loop until the target form is dismissed
	
	
	     Do While frmTarget.Visible = True
	     DoEvents
	     Loop
	
	     'FIX: Unload the Form
	     UnLoad frmTarget
	
	     'We have left the loop, so the dialog has been closed
	     'Now Enable the forms that were disabled, and exit the procedure
	
	     For Each ofrm In c
	         ofrm.Enabled = True
	     Next ofrm
	
	     End Sub
	
	Because a non-modal form cannot be shown from a modal form, the routine above
	must also be used to show the form prior to the modal form containing the DBGrid
	control.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start a new project in the 32-bit edition of Microsoft Visual Basic. Form1 is
	  created by default.
	
	2. From the Insert menu, select MDI Form to insert an MDI Parent form.
	
	3. From the Insert menu, select Form to insert two more regular forms into the
	  project.
	
	4. Choose Form1, and select the Properties window by pressing F4. Change the
	  MDIChild property to True.
	
	5. Place a Command button in Form1, and in the Click event place the following
	  code:
	
	     Private Sub Command1_Click()
	        Form2.Show vbModal
	     End Sub
	
	6. Place a Command button on Form2, and in the Click event, place the following
	  code:
	
	     Private Sub Command1_Click()
	        Form3.Show vbModal
	     End Sub
	
	7. On Form3, place a DBGrid control and a Data Control. Change the Databasename
	  property of the Data control to "biblio.mdb" in the Visual Basic directory.
	  Change the Recordsource property of the Data control to "Authors." Change the
	  Datasource property of the DBGrid control to "Data1."
	
	8. Run the project by pressing F5. Press the Command button on Form1 to show
	  Form2 modally. Press the Command button on Form2 to show Form3 modally. Close
	  Form3 using the Control box of the window. Note that Form2 flashes, and the
	  program hangs.
	
	To correct the problem in the Steps to Reproduce Problem section above, paste the
	ShowModalForm routine contained above into a standard code module, and then
	change the Command1_Click event in Form1 to:
	
	
	     'FIX: Flag to avoid unloading the form when the user closes it
	     Private mblnIgnoreUnload as boolean
	
	     'FIX: Additional Code for Form_Load of Form2
	     Private Sub Form_Load
	         mblnIgnoreUnload = True
	     End Sub
	
	     'FIX: Additional Code for Form_QueryUnLoad of Form2
	     Private Sub Form_QueryUnLoad
	         If mblnIgnoreUnload Then
	             Me.Hide ' Make Form2 Invisible
	             Cancel = True ' Do not unload Form2
	             mblnIgnoreUnload = False ' Next time we come here unload Form2
	         End If
	     End Sub
	
	     Private Sub Command1_Click()
	        ShowModalForm Form2
	     End Sub
	
	and change the Command1_Click event in Form2 to:
	
	     Private Sub Command1_Click()
	        ShowModalForm Form3
	     End Sub
	
	Now the forms correctly display and act like Modal forms, but the program does
	not hang when Form3 is dismissed.
	
	Additional query words: 4.00 vb4win vb4all buglist4.00
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400
	Version           : 4.00
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
