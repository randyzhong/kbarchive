---
layout: page
title: "Q150075: FIX: False Memory Leaks in MFC DLL Statically Linked to MFC"
permalink: /kb/150/Q150075/
---

## Q150075: FIX: False Memory Leaks in MFC DLL Statically Linked to MFC

{% raw %}

	Article: Q150075
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.0,4.1
	Operating System(s): 
	Keyword(s): kbProgramming kbDLL kbMFC kbVC400bug kbVC410bug kbVC420fix kbGrpDSMFCATL kbNoUpdatekbbu
	Last Modified: 03-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An MFC Regular DLL that is statically linked to the MFC library reports a memory
	leak although the memory is deallocated correctly in the destructor of the
	CWinApp-derived object in the DLL. An error message occurs:
	
	  "Detected memory leaks!
	  Dumping objects ->
	  D:\ProjDir\TheProj\TheProj.cpp(30) : {32} normal block at 0x00751FD0,
	  1000 bytes long."
	
	This may also happen for memory that is not deallocated until the destructor of
	any other global or static object in the DLL.
	
	CAUSE
	=====
	
	This is a false memory leak. In a Regular DLL statically linked to MFC, the
	debug memory heap is checked for leaks before the destructors are called for any
	global or static objects in the DLL.
	
	RESOLUTION
	==========
	
	Any deinitialization required for the DLL, when it is being unloaded or when its
	application has terminated, should be done in the ExitInstance member function
	of the Regular DLL's CWinApp-derived class.
	
	ExitInstance is called during the unloading of an MFC DLL but before the debug
	memory leak detection occurs. Memory allocations freed at this time do not get
	reported as false memory leaks.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem has been fixed in Visual C++ version
	4.2.
	
	MORE INFORMATION
	================
	
	This is an issue of timing.
	
	An MFC Regular DLL and an MFC application both have a global object declared at
	file-scope that is of a class derived from CWinApp. This is called the
	application object. The C Runtime is responsible for calling the destructors of
	all global and static objects. This is done after all other processing in the
	application or DLL is finished.
	
	The MFC framework calls the C Runtime function _CrtDumpMemoryLeaks() to detect
	memory leaks. This also happens during termination of the DLL or application.
	Normally, _CrtDumpMemoryLeaks is called automatically when an internal MFC
	process-local object, _AFX_DEBUG_STATE, is destructed by a call to
	AfxTermLocalData. This internal process-local object destructs when MFC itself
	is terminated and cleaned up.
	
	When MFC is used in the shared MFC40 DLL, the cleanup of MFC occurs during the
	unloading of this DLL, which always occurs after the termination of applications
	or DLLs that use it. However, when MFC is linked into a DLL or application, MFC
	is physically inside the DLL or application, and its cleanup occurs at the same
	time as the cleanup of global and static objects. For an MFC application, this
	is no problem. AfxTermLocalData (which eventually causes _CrtDumpMemoryLeaks to
	be called) is called from the destruction of a global object that is reliably
	destructed after any user-defined objects, due to the #pragma init_seg(lib)
	directive.
	
	However, Regular DLLs statically linked to MFC call AfxTermLocalData during
	DLL_PROCESS_DETACH in the DllMain function. DllMain is called by the C Run time
	before the C Run time destroys any global or static objects. Therefore, the
	order of execution would be:
	
	  DLLMAIN -> AfxTermLocalData -> ~_AFX_DEBUG_STATE ->
	  _CrtDumpMemoryLeaks
	
	which detects that some memory has yet to be freed. Then:
	
	  C Runtime cleanup (doexit) -> ~CWinApp
	
	where the program is finally and correctly freeing the memory.
	
	Putting memory deallocation and other deinitialization into the ExitInstance
	member function fixes the false memory leak detection because ExitInstance is
	called from DllMain before AfxTermLocalData is called.
	
	(c) Microsoft Corporation 1999, All Rights Reserved.
	Contributions by Jason Strayer, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbProgramming kbDLL kbMFC kbVC400bug kbVC410bug kbVC420fix kbGrpDSMFCATL kbNoUpdate kbbuglist kbfixlist
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:4.0,4.1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
