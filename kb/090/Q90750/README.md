---
layout: page
title: "Q90750: Windows Err Msg: Cannot Find a Device File that May Be..."
permalink: /kb/090/Q90750/
---

## Q90750: Windows Err Msg: Cannot Find a Device File that May Be...

{% raw %}

	Article: Q90750
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): MS-DOS:6.2,6.21; WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	- Microsoft MS-DOS operating system versions 6.2, 6.21 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The following error message may be displayed when you attempt to start Windows
	in enhanced mode:
	
	  Cannot find a device file that may be needed to run Windows in 386 Enhanced
	  Mode.
	
	In Windows 3.0 and 3.0a, the message is followed by a "run Setup again" message.
	In Windows 3.1, the message is followed by a "You need to run the Setup program
	again" message, and may specify the device filename.
	
	CAUSE
	=====
	
	The above error indicates that an entry specified in the [386Enh] section of the
	SYSTEM.INI file is invalid or cannot be located.
	
	There are two different types of device files that can be specified in the
	[386Enh] section on a DEVICE= line: internal and external. Internal device
	drivers are specified by an asterisk (*) before the device name, and are
	internal to the core Windows files (namely WIN386.EXE). External device drivers
	are usually specified by a .386 extension, and are located in the Windows SYSTEM
	subdirectory or in the path specified on the DEVICE= line. External virtual
	device drivers can be provided by Windows or by third- party products.
	
	WORKAROUND
	==========
	
	In general, reinstalling Windows is the best solution. This ensures the proper
	location of device drivers internally and externally provided by Windows. If a
	third-party device driver is causing the error, you need to reinstall the
	third-party program as well or rename SYSTEM.INI before reinstalling Windows so
	that the third-party product's changes are preserved.
	
	MORE INFORMATION
	================
	
	The following are specific problems and their solutions.
	
	EBIOS=X:*EBIOS
	--------------
	
	In some cases, you will get this error message due to the following line in the
	[386Enh] section of the SYSTEM.INI file:
	
	       ebios=x:*ebios
	
	To correct this problem, remove the "x:" from this line.
	
	The "x:" is used in the SETUP.INF file to refer to the disk containing the file
	WIN386.EXE. In some cases, this "x:" gets copied to the SYSTEM.INI during
	installation and is never removed.
	
	Windows 3.0 Files in a Windows 3.1 Installation
	-----------------------------------------------
	
	If the device driver causing the error is one or more of the following:
	
	  VTDAPI.386
	  INT13
	  WDCTRL
	  BLOCKDEV
	  KRNL386.EXE
	
	the error possibly indicates that Windows 3.1 has found core Windows 3.0 or 3.0a
	files in the WINDOWS or WINDOWS\SYSTEM subdirectory. Remove any core Windows 3.0
	or 3.0a files (specifically, WIN386.EXE) from these directories, and replace
	them by expanding the appropriate 3.1 files.
	
	PC Tools Version 7.0
	--------------------
	
	During PC Tools installation, version 7.0 of Central Point Software's PC Tools
	modifies the SYSTEM.INI file. It changes two DEVICE= statements in the [386Enh]
	section.
	
	After PC Tools installs, two device statements are changed from
	
	     device=*vdmad
	     device=*vfd
	
	to:
	
	     device=vdmad.386
	     device=vfd.386
	
	There are two ways to correct this problem:
	
	- Manually modify these two device statements in the [386Enh] section of
	  SYSTEM.INI to read as follows:
	
	        device=*vdmad
	        device=*vfd
	
	  -or-
	
	- Copy VDMAD.386 and VFD.386 from the PC Tools 7.0 disk to the Windows \SYSTEM
	  subdirectory.
	
	NOTE: A similar problem affecting only the VFD line occurs in version 8.0 of PC
	Tools. Use the same workaround to correct the problem.
	
	WINDEBUG.386
	------------
	
	If you installed the Windows Software Development Kit (SDK) for version 3.0 or
	3.1, you may receive this error as well. It indicates that Windows is unable to
	find the WINDEBUG.386 device driver because it is not in the path. This device
	is added by SDK Setup and is referenced by the DEVICE=WINDEBUG.386 line in the
	[386Enh] section of SYSTEM.INI.
	
	To resolve this problem, use a text editor such as Notepad to edit your
	AUTOEXEC.BAT file and add the SDK directory to the MS-DOS PATH. The default SDK
	directory is WINDEV.
	
	PCTools is manufactured by Central Point Software, a vendor independent of
	Microsoft; we make no warranty, implied or otherwise, regarding this product's
	performance or reliability.
	
	SMARTDrive /X Switch
	--------------------
	
	This error message may appear if you use the SMARTDrive /X switch (which ships
	with Microsoft MS-DOS version 6.2).
	
	Deleting the /X switch resolves the problem.
	
	Additional query words: 3.10 3.00 3.00a 6.2 6.20 "Unable To Find File Necessary Run Windows In 386 Enhanced Mode"
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311 kbMSDOSSearch kbMSDOS621 kbMSDOS620
	Version           : MS-DOS:6.2,6.21; WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
