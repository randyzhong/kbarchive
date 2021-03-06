---
layout: page
title: "Q196946: SNAOLEDB Fails with &quot;Data conversion (DCONV.DLL) not found&quot;"
permalink: /kb/196/Q196946/
---

## Q196946: SNAOLEDB Fails with &quot;Data conversion (DCONV.DLL) not found&quot;

{% raw %}

	Article: Q196946
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:1.0,4.0,4.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 19-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0 SP1 
	- Microsoft OLE DB Provider for AS/400 and VSAM, version 1.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Attempts to initialize the SNA Server OLE DB Provider for AS/400 or VSAM
	(SNAOLEDB) may fail with the following error message:
	
	  Data conversion (DCONV.DLL) not found
	
	This error may occur even though the Dconv.dll is present in the
	<snaroot>\System directory.
	
	CAUSE
	=====
	
	The SNA Server Dconv.dll is dependent upon the SNA Server version of Trnsdt.dll
	which SNA Server installs into the <sna>\System directory. If IBM Client
	Access is also installed on the computer, it installs its own version of
	Trnsdt.dll which conflicts with the SNA Server version, causing Dconv.dll to
	fail to initialize.
	
	This problem may occur with any version of the SNAOLEDB driver.
	
	RESOLUTION
	==========
	
	To solve the problem, rename the version of Trnsdt.dll located in the IBM Client
	Access directory, if it is installed on the computer. Only the SNA Server
	version of Trnsdt.dll should be present on the computer.
	
	NOTE: Renaming the IBM version of Trnsdt.dll may cause IBM Client Access
	applications to fail.
	
	If there are no duplicate versions of Trnsdt.dll present on the computer, ensure
	that there are no conflicting versions of these other dependent DLLs, and that
	these are available in the system path:
	
	Shipped with SNA Server:
	
	  Snanls.dll
	  Trnsdt.dll
	
	These are shipped by Windows NT:
	
	  Advapi32.dll
	  Gdi32.dll
	  Kernel32.dll
	  Ntdll.dll
	  Rpcrt4.dll
	  User32.dll
	
	This one is shipped by Windows NT and SNA Server, and may be redistributed by
	other applications too:
	
	  Msvcrt.dll
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbOLEDBSearch kbSNAServSearch kbOLEDBProvAS400VSAM100 kbSNAServ400 kbSNAServ400SP1 kbOLEDBProvSearch
	Version           : WINDOWS:1.0,4.0,4.0 SP1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
