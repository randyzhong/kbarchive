---
layout: page
title: "Q74717: Windows Err Msg: System Integrity Violation"
permalink: /kb/074/Q74717/
---

## Q74717: Windows Err Msg: System Integrity Violation

{% raw %}

	Article: Q74717
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	There are two major causes of System Integrity Violations:
	
	- There is a hardware conflict.
	
	  -or-
	
	- An MS-DOS application running under Windows is trying to access memory that
	  it does not have access to in Windows.
	
	MORE INFORMATION
	================
	
	If the System Integrity Violation error message occurs when you run a non-
	Windows application from Windows in enhanced mode, follow these steps:
	
	1. Use a AUTOEXEC.BAT file that looks like:
	
	        Path C:\Windows;C:\;C:\DOS
	        Prompt $p$g
	        Set Temp=C:\Windows\Temp
	
	  This example assumes that Windows is in C:\WINDOWS and that MS-DOS is in
	  C:\DOS.
	
	2. Use a CONFIG.SYS file that looks like:
	
	        Files=60
	        Buffers=10
	        Shell=c:\Command.com /p /e:2048
	        Device=c:\Himem.Sys
	
	  This example assumes HIMEM.SYS is in the root directory of drive C.
	
	3. Make sure the MS-DOS application is being called from a program information
	  file (PIF).
	
	4. Check to see if a System Integrity Violation still occurs. If it does,
	  continue with step 5. Otherwise, the application's problem was cleared up in
	  either the AUTOEXEC.BAT, CONFIG.SYS, or the PIF.
	
	5. Try running Windows in standard mode.
	
	6. If the program runs under Windows in standard mode, add these two lines to
	  the [386Enh] section of SYSTEM.INI and then try running Windows in enhanced
	  mode:
	
	        EmmExclude=A000-C7FF
	        EmmExclude=E000-EFFF (for some programs E000-FFFF)
	
	7. If step 5 does not work and your AUTOEXEC.BAT and CONFIG.SYS files read as
	  above, the application may be incompatible with Windows or you have a
	  hardware conflict of some type.
	
	Additional query words: 3.00 3.0 3.0a 3.00a tshoot
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a
	Version           : WINDOWS:3.0,3.0a
	
	=============================================================================
	

{% endraw %}
