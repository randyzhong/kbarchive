---
layout: page
title: "Q190198: BUG: VB Fails When Editing Modules That Are Interdependent"
permalink: /kb/190/Q190198/
---

## Q190198: BUG: VB Fails When Editing Modules That Are Interdependent

{% raw %}

	Article: Q190198
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When your project contains modules that are heavily dependent upon each other
	for variable definitions (such as a constant being the type of another module,
	or passing a UDT defined in one module to another), editing one module will
	gradually cause Microsoft Visual Basic to fail.
	
	CAUSE
	=====
	
	The problem is caused by an illegal circular dependency cycle between the
	modules.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new ActiveX DLL project in Visual Basic. Class1 is created by
	  default.
	
	2. Paste the following code in Class1:
	
	        Public Type UDT3
	           a As Class2
	           b As Class3
	        End Type
	
	        Public Enum Enum1
	           red
	        End Enum
	
	        Public Sub T(a As UDT3)
	        End Sub
	
	3. Add a class module (Class2) to the project, and paste the following code in
	  Class2:
	
	        Public Sub Test(a As Enum2)
	        End Sub
	        Public Sub Test2(a As Enum1)
	        End Sub
	
	4. Add a class module (Class3) to the project, and paste the following code into
	  Class3:
	
	        Public Enum Enum2
	           Green
	        End Enum
	
	        Private Const C1 = Enum1.red
	
	5. In Class1, add the following line of code as a third field to Type UDT3:
	
	        c as long
	
	Notice that Visual Basic fails after typing "c as ." It also crashes if you add a
	member to Enum1 in Class1 or add a procedure and then press the F5 key.
	
	Additional query words: kbDSupport kbdss kbVBp600bug kbVBp kbNoKeyWord
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
