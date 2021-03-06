---
layout: page
title: "Q190726: FIX: Visual C++ 5.0 #import Causes Errors with ADO Version 2.0"
permalink: /kb/190/Q190726/
---

## Q190726: FIX: Visual C++ 5.0 #import Causes Errors with ADO Version 2.0

{% raw %}

	Article: Q190726
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:2.0; winnt:5.0
	Operating System(s): 
	Keyword(s): kberrmsg kbADO200 kbVC500bug kbVC600fix
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	- ActiveX Data Objects (ADO), version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On a clean Windows 95 or Windows 98 machine with DCOM95 or DCOM98 installed,
	compile the following in a .cpp file:
	
	  #import "c:\program files\common files\system\ado\msado15.dll"
	
	RESULT: You get the following error messages:
	
	  
	
	  error C2504: '_Connection15' : base class undefined
	
	  
	
	  error C2504: '_Recordset15' : base class undefined
	
	  
	
	  error C2504: 'Fields15' : base class undefined
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Connection *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::_Recordset *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::Fields *const ' to 'struct IUnknown *'
	
	  
	
	  error C2664: '_com_issue_errorex' : cannot convert parameter 2 from
	               'struct ADODB::Fields *const ' to 'struct IUnknown *'
	
	NOTE: This problem also occurs on Windows NT 4.0, and the resolution given
	applies.
	
	CAUSE
	=====
	
	This is a problem in the #import feature of the compiler.
	
	RESOLUTION
	==========
	
	To work around this problem, use one of the following alternatives:
	
	- Install Visual Studio 97, Service Pack 3.
	
	- Upgrade to Visual C++, version 6.0.
	
	- Modify the resultant .tlh file by moving each of the declarations for
	
	  _Connection15, _Recordset15, and Field15
	
	  ahead of each of the declarations for
	
	  Connection, Recordset, and Field.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. The problem has been corrected in Visual Studio 97,
	Service Pack 3, and also in Visual C++ version 6.0.
	
	REFERENCES
	==========
	
	For additional information about how to obtain Visual Studio 97, Service Pack 3,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q170365 Visual Studio 97 Service Packs - What, Where, and Why
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbADO200 kbVC500bug kbVC600fix 
	Technology        : kbVCsearch kbAudDeveloper kbADOsearch kbADO200 kbVC500 kbVC32bitSearch kbVC500Search
	Version           : WINDOWS:2.0; winnt:5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
