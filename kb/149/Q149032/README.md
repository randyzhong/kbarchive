---
layout: page
title: "Q149032: PRB: VB 3.0 OLE Clients Do not Repaint Before OLE Call Returns"
permalink: /kb/149/Q149032/
---

## Q149032: PRB: VB 3.0 OLE Clients Do not Repaint Before OLE Call Returns

{% raw %}

	Article: Q149032
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbVBp400
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When calling a method or accessing a property of an OLE server from Visual Basic
	3.0, no painting takes place on any of the Visual Basic 3.0 forms that are
	showing. This behavior remains until the call to the OLE server method or
	property returns. This behavior occurs with OLE servers built in any
	environment, including, but not limited to, Visual Basic 4.0. OLE automation
	clients built with Visual Basic 4.0 do not show this characteristic.
	
	CAUSE
	=====
	
	To receive Windows paint messages while in a synchronous OLE call, an OLE
	automation client must implement the IMessageFilter interface. Visual Basic 3.0
	does not implement this interface, and so Visual Basic 3.0 windows cannot
	receive any paint messages until a synchronous call returns. Because Visual
	Basic 4.0 does implement this interface, painting can continue without problem
	before a call has returned.
	
	STATUS
	======
	
	This behavior is by design.
	
	
	MORE INFORMATION
	================
	
	Steps To Reproduce Problem
	--------------------------
	
	1. Following the instructions in Q129801, "How to Create and Use a Minimal OLE
	  Automation Server," create a simple OLE server with Visual Basic 4.0. To
	  obtain this article, query on the following words here in the Microsoft
	  Knowledge Base:
	
	  " vbwin and chocolates and step " (without the quotation marks)
	
	2. Add a single form to this OLE server project by clickng Form on the Insert
	  menu.
	
	3. Add this procedure to the class module in the OLE server project:
	
	        Public Sub ShowForm()
	           Form1.Show vbModal
	        End Sub
	
	4. Compile the OLE server project and exit Visual Basic 4.0.
	
	5. Start Visual Basic 3.0. Form1 is created by default.
	
	6. Add this code to the Form_Click event in the Visual Basic 3.0 project:
	
	        Sub Form_Click()
	           Dim o As Object
	
	           ' If the ProgID has been changed then modify it below.
	           Set o = CreateObject("Project1.Class1")
	           o.ShowForm
	           MsgBox "Method returned"
	        End Sub
	
	7. Press F5 or click Start on the Run menu to run the application. Click once on
	  the form and notice how no repainting occurs while the modal form displays.
	  Unloading the modal form causes the message box to display and also resumes
	  all Windows messages to the Visual Basic 3.0 project.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp400 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
