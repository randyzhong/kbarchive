---
layout: page
title: "Q84932: DLLSKEL Demonstrates DLL and Calling Application"
permalink: /kb/084/Q84932/
---

## Q84932: DLLSKEL Demonstrates DLL and Calling Application

{% raw %}

	Article: Q84932
	Product(s): Microsoft Windows Software Development Kit
	Version(s): 3.0,3.1
	Operating System(s): 
	Keyword(s): kbfile kbsample kb16bitonly kbOSWin310 kbOSWin300
	Last Modified: 23-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	DLLSKEL is a file in the Microsoft Download Center that contains the source code
	for a minimal dynamic-link library (DLL) for the Windows environment. DLLSKEL
	demonstrates how to correctly implement and compile a multiple-segment DLL.
	
	MORE INFORMATION
	================
	
	This sample has two parts: the multiple-segment DLL and an application for the
	Windows environment. The application has all the features of the Generic sample
	application provided with the Windows Software Development Kit and a menu item
	that calls a function exported from the DLL. The DLL function creates a message
	box when it is called by the application.
	
	The DLLSKEL sample demonstrates implicitly loading a DLL. However, the
	modifications required to explicitly load the DLL are straightforward.
	
	The following file is available for download from the Microsoft Download Center:
	
	  Dllskel.EXE
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	To properly implement a DLL, one must consider several program details. DLLSKEL
	demonstrates how to address all these details to create a simple DLL.
	
	In the DLLSKEL sample, the DLL has multiple code segments. The Windows exit
	procedure (WEP) is placed in a fixed segment while the remainder of the code is
	placed in movable, discardable segments. The WEP must reside in a fixed code
	segment so that it can be called at all times, even when the system has very
	little free memory. Consider the situation in which Windows has discarded the
	segment containing the WEP. When Windows calls the WEP, the segment must be
	loaded back into the system and all relocations to other segments must be fixed
	up, which might require other segments to be loaded. If the system does not have
	enough memory to load all the required segments, or if some of the segments no
	longer exist, Windows will report an unrecoverable application error (UAE) or
	general protection (GP) fault because it cannot completely load the segment
	containing the WEP. If the WEP is placed in a fixed code segment, the
	relocations are fixed up only once, which completely avoids this situation.
	
	The WEP was originally designed to allow a DLL that hooked an interrupt to unhook
	it before termination, not to provide a general-purpose cleanup procedure for a
	DLL. Under Windows 3.0, the WEP is called on a very small stack located in the
	Windows Kernel, which will overflow if the WEP calls Windows functions. There is
	enough room to unhook an interrupt, however. Under Windows 3.1, the WEP is
	called on a 4K stack in the Windows Kernel, which provides enough room to call
	Windows functions and to perform general DLL cleanup. Because the WEP is called
	only once during the lifetime of a DLL, it cannot be used to clean up each
	application instance that uses the DLL. Under Windows versions 3.0 and 3.1, if a
	DLL requires each application instance to call a cleanup routine, the DLL must
	explicitly provide the routine, which each application instance must explicitly
	call.
	
	An implicitly loaded DLL is loaded into memory before the calling application is
	completely loaded. Therefore, the LibMain() function, which is analogous to an
	application's WinMain() function, will be called before the application's
	message queue is initialized. Therefore, the DLL must not call functions that
	send messages to the application in LibMain(). Similarly, an implicitly loaded
	DLL is terminated after the calling application has been removed from memory.
	Therefore, nothing in the WEP must require the application to exist.
	
	The LoadLibrary() function loads a DLL explicitly; the FreeLibrary() function
	unloads a DLL. To modify DLLSKEL to explicitly load and free the DLL:
	
	1. Call the LoadLibrary() function to load the DLL. Save the library module
	  handle.
	
	2. Call the GetProcAddress() function, specifying the library module handle and
	  the name of the function, to retrieve the pointer to the DLL function.
	
	3. Call the FreeLibrary() function to free the DLL.
	
	4. Modify the makefile to remove the call to IMPLIB and remove DLLSKEL.LIB from
	  the linker command line.
	
	Additional query words: softlib DLLSKEL.EXE kbfile
	
	======================================================================
	Keywords          : kbfile kbsample kb16bitonly kbOSWin310 kbOSWin300 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : :3.0,3.1
	
	=============================================================================
	

{% endraw %}
