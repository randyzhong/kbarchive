---
layout: page
title: "Q45718: PRB: Addressing L1064: &quot;Out of Memory&quot; Errors"
permalink: /kb/045/Q45718/
---

## Q45718: PRB: Addressing L1064: &quot;Out of Memory&quot; Errors

{% raw %}

	Article: Q45718
	Product(s): Microsoft Programming Utilities
	Version(s): MS-DOS:5.03,5.05,5.1,5.13,5.3,5.31.009,5.5; OS/2:5.03,5.05,5.1,5.13
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 24-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft LINK for MS-DOS, versions 5.03, 5.05, 5.1, 5.13, 5.3, 5.31.009, 5.5 
	- Microsoft LINK for OS/2, versions 5.03, 5.05, 5.1, 5.13 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An attempt to link an application fails and Microsoft LINK generates the
	following message:
	
	  L1064: Out of memory
	
	CAUSE
	=====
	
	According to the "Microsoft FORTRAN, Microsoft CodeView and Utilities User's
	Guide" for version 5.0 the causes of this error are as follows:
	
	  The linker was not able to allocate enough memory from the operating system
	  to link the program. On OS/2 try increasing the swap space. Otherwise, reduce
	  the size of the program in terms of code, data, and symbols. On OS/2,
	  consider splitting the program into dynalink libraries.
	
	RESOLUTION
	==========
	
	The methods to work around this error depend on the operating system in which
	LINK is running. In the MS-DOS operating system, the two methods to address this
	situation are as follows:
	
	- Remove any unnecessary memory-resident software or device drivers that limit
	  the amount of free memory.
	
	- Reduce the size of the application as described above.
	
	If you are using LINK version 5.3 or later in the MS-DOS or Microsoft Windows
	operating systems, the seven methods to address this situation are as follows:
	
	1. Delete unnecessary files to free space on your hard disk.
	
	2. Increase the size of the Windows swap file. To create the largest possible
	  swap file, use a disk defragmentation utility to make the free space
	  contiguous.
	
	3. Reduce the size of the code, data, or symbols.
	
	4. If the program is a segmented-executable file, place some of its code into a
	  dynamic-link library (DLL).
	
	5. Remove unnecessary terminate-and-stay-resident (TSR) software.
	
	6. Reconfigure the Expanded Memory Manager to provide more conventional memory.
	
	7. Edit the CONFIG.SYS file to specify fewer buffers in the BUFFERS statement or
	  fewer drives in the LASTDRIVE statement.
	
	In the OS/2 operating system, the easiest method to work around this error is
	perform the following three steps to increase the swap space:
	
	1. Free up RAM and swap space by closing other screen groups and removing other
	  processes from memory.
	
	2. Load the CONFIG.SYS file into an editor. Find the SWAPPATH statement and
	  determine the hard disk on which OS/2 stores the swap file. Delete one or
	  more files from this hard disk or modify the SWAPPATH statement to point to a
	  drive with more free space.
	
	3. If the error persists, carefully read the explanation of the SWAPPATH setting
	  in the text below and possibly decrease the swap value specified in the
	  SWAPPATH setting.
	
	MORE INFORMATION
	================
	
	The L1064: "Out of memory" error was introduces in LINK version 5.03 which was
	first provided with the IMSL libraries for Microsoft FORTRAN version 4.1 and was
	also provided with FORTRAN version 5.0.
	
	Explanation of the SWAPPATH Setting in CONFIG.SYS
	-------------------------------------------------
	
	The MEMMAN setting in CONFIG.SYS must enable swapping for the SWAPPATH setting to
	be acknowledged at all (typically, the command is "MEMMAN=SWAP" or
	"MEMMAN=SWAP,MOVE").
	
	The default SWAPPATH setting when OS/2 is first installed is usually as follows:
	
	  SWAPPATH=C:\OS2\SYSTEM 512
	
	The file specification indicates the drive and directory where the swap file is
	allocated. If the CONFIG.SYS file does not contain a SWAPPATH variable, the
	swapper allocates space in the root directory on the boot drive. The numeric
	parameter indicates the amount of free space that must remain on this drive when
	the swap file grows to its maximum size. (By itself, this number does not
	indicate the maximum size of the swap file.) Given the SWAPPATH statement above,
	the maximum size of the swap file is calculated as follows:
	
	  (free space on drive C) - 512K = (maximum swap file size)
	
	Therefore, increasing the value in the SWAPPATH statement DECREASES the amount of
	memory available for the swap file.
	
	You can decrease the value in the SWAPPATH setting and the system allows values
	as low as 0 (zero). However, because OS/2 shares processor time between
	processes and may need to write to the disk that contains the swap file,
	decreasing the SWAPPATH value below 512K (the system default) is not
	recommended. Reduce the value only if the SWAPPATH statement specifies a value
	greater than 512K (the valid range is 0 to 32,767). If this is the case, use a
	text editor to edit CONFIG.SYS and set the SWAPPATH value to Shutdown and reboot
	the machine.
	
	If the problem persists, you must delete files from the hard disk that contains
	the swap file.
	
	Additional query words: 5.03 5.05 5.10 5.13 5.30 5.31.009 5.50
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbZNotKeyword3 kbLINKSearch kbLINK503DOS kbLINK510DOS kbLINK513DOS kbLINK530DOS kbLINK53109DOS kbLINK550DOS kbLINK503OS2 kbLINK505OS2 kbLINK510OS2 kbLINK513OS2 kbLINK505DOS
	Version           : MS-DOS:5.03,5.05,5.1,5.13,5.3,5.31.009,5.5; OS/2:5.03,5.05,5.1,5.13
	
	=============================================================================
	

{% endraw %}
