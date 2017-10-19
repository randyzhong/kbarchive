---
layout: page
title: "Q275490: Debugger Symbol Loading Facility Cannot Load SP6 Kernel Symbols"
permalink: kb/275/Q275490/
---

## Q275490: Debugger Symbol Loading Facility Cannot Load SP6 Kernel Symbols

	Article: Q275490
	Product(s): Microsoft Windows NT
	Version(s): 4.0,4.0 SP6,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbDebug
	Last Modified: 03-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0, 4.0 SP6a 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP6a 
	- Microsoft Windows NT Server versions 4.0, 4.0 SP6, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The symbol server technology (referred to as Symsrv.dll) included with the new
	Microsoft Debugger Tools, indexes symbols by file size and timestamp. When you
	debug and your debugger is configured to use a custom-built symbol server, you
	find that the debugger complains about symbol mismatch for kernel symbols that
	you know are correct.
	
	CAUSE
	=====
	
	This behavior can occur because all of the Microsoft Windows NT 4.0 Service Pack
	6 (SP6) kernels have an incorrect file size written to the image header of the
	symbols. Symsrv.dll must guarantee an exact match of the file size and timestamp
	or it cannot load the symbol.
	
	RESOLUTION
	==========
	
	To resolve this behavior, you can follow one of two methods:
	
	Method 1:
	---------
	
	You can point the debugger to the Windows NT 4.0 SP6 kernel symbols by means of a
	symbol path that points to a static symbol tree or places the path to the static
	symbol tree first in its symbol path.
	
	Method 2:
	---------
	
	You can adjust the directory name in the Symsrv directory tree for the component
	in question.
	
	To perform this method, you must find the calculated signature of the module that
	Symsrv.dll wants. Use the Symbol Noisy mode of the debugger by specifying the -n
	switch on the command line of the debugger. The following output is an example
	of sample output in Noisy mode:
	
	  
	
	  Loading symbols for 80100000     Ntkrnlmp.exe ->   Symsrv: \\Nissi\Symsrv
	  \Ntkrnlmp.dbg\37e80077df000\Ntkrnlmp.dbg - file not found.
	  Symsrv: \\Nissi\Symsrv\Ntkrnlmp.pdb\0\Ntkrnlmp.pdb - file not found.
	
	Next, search the directory tree of the Symsrv folder, under the module you want,
	for example:
	
	  
	
	  P:\Symsrv\Ntkrnlmp.dbg>dir
	Volume in drive P is CARK
	Volume Serial Number is A8BF-2445
	
	Directory of P:\symsrv\ntkrnlmp.dbg
	
	  10/24/2000  02:28p      -DIR-          .
	  10/24/2000  02:28p      -DIR-          ..
	  10/20/2000  05:23p      -DIR-          3255a937d80c0
	  10/20/2000  05:27p      -DIR-          3571ec24eec40
	  10/20/2000  04:35p      -DIR-          37e80077e8600
	  10/20/2000  05:17p      -DIR-          384d5a761897c0
	  10/20/2000  04:53p      -DIR-          38f222cbf3d40
	  10/20/2000  04:29p      -DIR-          3975dfdf199980
	              0 File(s)              0 bytes
	              8 Dir(s)   2,570,076,160 bytes free
	
	NOTE: The value of the signature generated by the debugger at the run time
	(37e80077df000) and the value of the signature generated by Symstore from data
	in the header of the symbol (37e80077e8600) share the first eight digits as read
	from left to right.
	
	When you have found this match (the first eight digits), verify that the symbol
	is the one you want by looking in the File.ptr file, for example:
	
	  
	
	  P:\Symsrv\Ntkrnlmp.dbg\37e80077e8600>type File.ptr
	  \\Nissi\Symtree\1381.sp6.i386\Symbols\Exe\Ntkrnlmp.dbg
	
	To correct the behavior, rename the 37e80077e8600 directory to 37e80077df000.
	
	NOTE: Repeat the preceding steps for all of the SP6 kernels.
	
	MORE INFORMATION
	================
	
	The debuggers can load symbols by means of a standard static symbol path or by
	means of the new Symsrv.dll (for example, _nt_symbols_path=symsrv
	*Symsrv.dll*\\Symserver \Share), or any combination of the two types of paths.
	When you use a static symbol path, the debugger does not need to match both the
	file size and timestamp in the header in order to load a symbol.
	
	Microsoft shipped the retail version of the new Microsoft Debugger Tools on
	September 21, 2000.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDebug 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400sp6 kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServ400sp6 kbNTTermServSearch kbWinNTSEnt400SP6a
	Version           : :4.0,4.0 SP6,4.0 SP6a
	Issue type        : kbprb
	
	=============================================================================
	