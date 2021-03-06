---
layout: page
title: "Q81493: Using VCPI Programs with Windows"
permalink: /kb/081/Q81493/
---

## Q81493: Using VCPI Programs with Windows

{% raw %}

	Article: Q81493
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 05-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Many MS-DOS-based applications use the Virtual Control Program Interface (VCPI)
	specification to directly access protected-mode extended memory on an 80386 or
	80486 computer. These programs do not work with Microsoft Windows version 3.0 in
	386 enhanced mode. They work in Windows in real mode and may work in standard
	mode. Windows uses a newer standard called DOS Protected Mode Interface (DPMI).
	
	DPMI is a multitasking version of VCPI with a few other enhancements. Many
	software companies have already announced plans to support DPMI in future
	releases of their products. If you experience difficulties running an MS-
	DOS-based application in standard or enhanced mode of Windows, check with the
	MS-DOS-based-application manufacturer to see if it now supports the DPMI
	specification.
	
	MORE INFORMATION
	================
	
	The following switch can be entered into the SYSTEM.INI file in the [386Enh]
	section to turn off the warning message that appears when an MS-DOS-based
	application attempts to use VCPI:
	
	  VCPIWarning=false
	
	NOTE: Changing this switch does not allow the application to run. It merely
	suppresses the warning message if you attempt to run one of these applications.
	
	The following is a partial list of applications that use the VCPI specification
	to access extended memory:
	
	  Application                          Vendor
	  --------------------------------------------------------------------
	  Lotus 1-2-3 release 3.0              Lotus
	  Interleaf Publisher                  IBM
	  Autocad 386                          Autodesk
	  Paradox 386                          Borland
	  FoxBase+ 386                         Microsoft
	  Smalltalk 80 386                     ParcPlace
	  Common Lisp CLOE-386                 Symbolics
	  Laboratory Microsystems UR/Forth     STSC
	  APL Plus II                          STSC
	  VM/386                               Intelligent Graphics Corporation
	  Concurrent DOS 386                   Digital Research
	  PC-MOS/386                           The Software Link
	
	Lotus has announced that version 3.1 will follow the DPMI specifications and will
	run under all three modes of Windows 3.0.
	
	PC-MOS is a multitasking operating environment similar to Windows/386. You cannot
	run Windows under PC-MOS because Microsoft Windows/286, Windows/386, and Windows
	3.0 and 3.1 are all protected-mode software competing for the same resources.
	
	The following is a list of 386 memory managers that use the VCPI specification
	and are incompatible with Windows 3.0 running in enhanced mode:
	
	  Memory Manager                       Vendor
	  --------------------------------------------------------------------
	  ILIM386.SYS                          Intel
	  Soft Bits 386                        Soft Bits
	  CEMM                                 COMPAQ Computer Company
	  QEMM                                 Quarterdeck Office Systems
	  386-to-the-Max                       Qualitas
	
	Most of the companies listed above are also planning versions of their
	applications that will use the DPMI specification.
	
	Additional query words: 3.00 3.0 3.0a 3.00a VCPI DPMI 3.10 3.1 winmem win31 3.11
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311
	Version           : WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
