---
layout: page
title: "Q79857: Communal Data Is Not Included in the LIB Listing"
permalink: kb/079/Q79857/
---

## Q79857: Communal Data Is Not Included in the LIB Listing

	Article: Q79857
	Product(s): Microsoft Programming Utilities
	Version(s): MS-DOS:3.11,3.17,3.18,3.2,3.20.010,3.31,3.4; OS/2:3.11,3.17,3.18
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 30-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft LIB for MS-DOS, versions 3.11, 3.17, 3.18, 3.2, 3.20.010, 3.31, 3.4 
	- Microsoft LIB for OS/2, versions 3.11, 3.17, 3.18 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Communal data declarations generate no PUBLIC definitions. Therefore, although
	they can be placed in a library, they are not placed in the library dictionary
	and will not be a part of the library listing generated by the LIB utility.
	
	MORE INFORMATION
	================
	
	Communal variables are supported only by QuickC, Microsoft C versions 5.0 and
	later, and MASM. They are, however, similar to common blocks in FORTRAN. In C,
	communal variables are the uninitialized global data items. In MASM, they are
	data items declared with the COMM qualifier.
	
	The linker will assume the communal variables refer to an external defining
	declaration elsewhere. If there is no external definition, the linker allocates
	storage and initializes it to 0 (zero). If there is more than one declaration,
	storage is allocated for the largest data item declared. For example, if I is
	declared int I; in one module and char I; in another module, the linker will
	allocate 2 bytes for I because the int is 2 bytes but the char is only 1 byte.
	Because memory for communal variables may not be assigned until load time, their
	use may reduce the size of your executable file.
	
	When a communal variable is declared in a library and defined in one of the
	object modules, references to that variable will be resolved with the defined
	variable. For this reason, communal variable declarations are not recommended
	for any file that might be placed in a library. If a variable defined in a .OBJ
	file accidentally had the same name as a communal variable in a library that it
	is being linked with, its value would unexplainably change every time you called
	a library function that used that communal variable! The linker does not issue a
	warning because the variable was defined only once, in the OBJ file.
	
	In addition, a communal data item X in a library cannot be used to resolve an
	external reference to X in a module linked with that library. For example,
	linking the following:
	
	     C File            Module in Library
	     ------            -----------------
	    
	     extern int X;           int X;
	
	        void main(void)
	        {
	           X = 5;
	        }
	
	would still result in the error:
	
	  L2029 'X': unresolved external
	
	Additional query words: kbinf 3.11 3.17 3.18 3.20, 3.20.01 3.31 3.40
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbVCsearch kbAudDeveloper kbLibSearch kbZNotKeyword3 kbLibMan318DOS kbLibMan311DOS kbLibMan317DOS kbLibMan320DOS kbLibMan320010DOS kbLibMan331DOS kbLibMan340DOS kbLibMan311OS2 kbLibMan317OS2
	Version           : MS-DOS:3.11,3.17,3.18,3.2,3.20.010,3.31,3.4; OS/2:3.11,3.17,3.18
	
	=============================================================================
	