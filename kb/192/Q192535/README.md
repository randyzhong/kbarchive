---
layout: page
title: "Q192535: PRB: Regsvr32.exe Fails in Mfco42d.dll Registering MFC Server"
permalink: /kb/192/Q192535/
---

## Q192535: PRB: Regsvr32.exe Fails in Mfco42d.dll Registering MFC Server

{% raw %}

	Article: Q192535
	Product(s): Microsoft C Compiler
	Version(s): winnt:5.0,6.0
	Operating System(s): 
	Keyword(s): kbole kbDebug kbMFC kbVC500 kbVC600 kbGrpDSMFCATLkbfaq
	Last Modified: 21-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Regsvr32 may fail when registering a debug build of an MFC Server. The error
	message box may contain the following message:
	
	  The ordinal 3300 could not be located in the dynamic link library
	  MFCO42D.DLL.
	
	The ordinal number may vary.
	
	If you click OK, another error message may appear stating:
	
	  RegSvr32: LoadLibrary("<server name>") failed.
	  GetLastError returns 0x000000b6.
	
	CAUSE
	=====
	
	The error occurs because the Debug MFC DLL's are not binary-compatible between
	Visual C++ 5.0 and Visual C++ 6.0. If the user has written a debug build DLL in
	Visual C++ 5.0 and attempts to register it on a machine that has Visual C++ 6.0,
	then the error will appear.
	
	RESOLUTION
	==========
	
	The following are three possible workarounds:
	
	- Build a release version of the server in Visual C++ 5.0 and run it on the
	  target Visual C++ 6.0 machine.
	
	- Rebuild the Server using Visual C++ 6.0.
	
	- Copy the MFC debug DLLs from VC++ 5.0 to the same directory on the target
	  machine as the MFC ActiveX server (for diagnostic purposes only because
	  redistribution violates the Visual C++ license agreement).
	
	STATUS
	======
	
	This behavior is by design.
	
	REFERENCES
	==========
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q190487 PRB: MFC Debug DLLs Are Not Compatible Between Versions
	
	Additional query words: 3304
	
	======================================================================
	Keywords          : kbole kbDebug kbMFC kbVC500 kbVC600 kbGrpDSMFCATL kbfaq
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
