---
layout: page
title: "Q198707: SMS: Dependency Walker for Win32 (Depends.exe)"
permalink: /kb/198/Q198707/
---

## Q198707: SMS: Dependency Walker for Win32 (Depends.exe)

{% raw %}

	Article: Q198707
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): kbtool
	Last Modified: 19-MAY-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the Depends.exe tool that is included with Microsoft
	Visual Studio 6.0 and Microsoft Windows NT 4.0 Resource Kit Supplement 3 and
	later. You can use this tool to assist in diagnosing problems with a particular
	.dll or .exe file.
	
	MORE INFORMATION
	================
	
	Dependency Walker for Win32 (Depends.exe) is a diagnostic tool that that you can
	use to determine which 32-bit program files are required to run a particular
	program or load a particular dynamic-link library (DLL). The Depends.exe
	features include:
	
	- The minimum set of files required to run a particular program or load a
	  particular DLL.
	
	- Why a certain module is being loaded with a particular program.
	
	- The complete path for all the modules being loaded for a particular program.
	
	- The base addresses of each module being loaded.
	
	- The version of the file and/or computer type that it was created for.
	
	Dependency Walker recursively scans all dependent modules required by a
	particular program. During this scan it performs the following tasks:
	
	- Detects missing files. These are files that are required as a dependency to
	  another module. A symptom of this problem is the "The dynamic link library
	  Bar.dll could not be found in the specified path..." error message.
	
	- Detects invalid files. This includes files that are not Win32 compliant and
	  files that are corrupted. A symptom of this problem is the "The program or
	  DLL Bar.exe is not a valid Windows image" error message.
	
	- Detects import/export mismatches. The tool verifies that all functions
	  imported to a module are actually exported from the dependent modules. All
	  unresolved import functions are flagged with an error message. A symptom of
	  this problem is the "The procedure entry point Name could not be located in
	  the dynamic link library Bar.dll" error message.
	
	- Detects circular dependency errors. This is a very rare error, but it can
	  occur with forwarded functions.
	
	- Detects mismatched computer module types. This occurs if a module built for
	  one type of computer tries to load a module built for a different type of
	  computer.
	
	You can run this tool from a command prompt or from within Windows.
	
	The syntax of the command is: depends.exe
	
	Additional query words: prodsms smstools
	
	======================================================================
	Keywords          : kbtool 
	Technology        : kbSMSSearch kbSMS200
	Version           : winnt:2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
