---
layout: page
title: "Q40184: NMAKE Builds Only the First Target in Makefile"
permalink: /kb/040/Q40184/
---

## Q40184: NMAKE Builds Only the First Target in Makefile

{% raw %}

	Article: Q40184
	Product(s): Microsoft Programming Utilities
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-JAN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft NMAKE Utility for MS-DOS 
	- Microsoft NMAKE Utility for OS/2 
	- Microsoft NMAKE Utility for Windows NT 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	By default, the NMAKE file maintenance utility builds only the first target in a
	makefile, if the command line does not explicitly list a target to build. The
	MAKE file maintenance utility defaults to building each target listed in the
	makefile.
	
	MORE INFORMATION
	================
	
	The following code example demonstrates this behavior. The MAKE utility compiles
	PROG1.C and links PROG1.OBJ while the NMAKE utility only compiles PROG1.C. This
	is an important consideration when you port a makefile from MAKE to NMAKE.
	
	Sample Code
	-----------
	
	       # Build options required: None
	
	     PROG1.OBJ : PROG1.C
	         cl /Zi /c PROG1.C
	
	     PROG1.EXE : PROG1.OBJ
	         link /CO PROG1.OBJ
	
	If all files are out-of-date with respect to PROG1.C and the NMAKE command line
	is as follows
	
	  NMAKE /f makefile
	
	the NMAKE utility executes only the following command:
	
	  cl /Zi /c prog1.c
	
	NMAKE defaults to building only the first target in the makefile. To achieve the
	desired results, specify the desired target, PROG1.EXE, on the NMAKE
	command-line or modify the makefile to add the following line to the beginning
	of the file:
	
	  ALL : PROG1.EXE
	
	NMAKE builds the pseudotarget "ALL" because it is the first target in the
	makefile. Using a pseudotarget causes NMAKE to build all the dependencies
	because the pseudotarget is always out-of-date.
	
	REFERENCES
	==========
	
	For more information, see the NMAKE documentation provided with your compiler or
	assembler.
	
	Additional query words: kbinf 1.20 1.30 1.40 1.50
	
	======================================================================
	Keywords          :  
	Technology        : kbVCsearch kbAudDeveloper kbNMAKESearch
	Version           : :
	
	=============================================================================
	

{% endraw %}
