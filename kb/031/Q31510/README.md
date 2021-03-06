---
layout: page
title: "Q31510: INFO: Bitwise Complement Operator Appears to Fail on Comparison"
permalink: /kb/031/Q31510/
---

## Q31510: INFO: Bitwise Complement Operator Appears to Fail on Comparison

{% raw %}

	Article: Q31510
	Product(s): Microsoft C Compiler
	Version(s): MS-DOS:6.0,6.00a,6.00ax,7.0; OS/2:6.0,6.00a; WINDOWS:1.0,1.5; WINDOWS NT:1.0,2.0,4.0,5.
	Operating System(s): 
	Keyword(s): kbCompiler kbVC100 kbVC150 kbVC200 kbVC400 kbVC500 kbVC600
	Last Modified: 22-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C/C++ Compiler (CL.EXE), included with:
	   - Microsoft C for MS-DOS, versions 6.0, 6.0a, 6.0ax 
	   - Microsoft C for OS/2, versions 6.0, 6.0a 
	   - Microsoft C/C++ for MS-DOS, version 7.0 
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5 
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 4.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The bitwise complement operator (~) appears to work incorrectly when an
	application uses it to compare unsigned characters.
	
	CAUSE
	=====
	
	Before the compiler uses the bitwise complement operator, it performs the "usual
	arithmetic conversions" which are described in detail in the "C Language
	Reference" manual.
	
	RESOLUTION
	==========
	
	Cast the complemented operand to an unsigned character. This prevents the
	compiler from performing the arithmetic conversions.
	
	MORE INFORMATION
	================
	
	The following code example returns the value "failed" even though it appears
	that values "j" and "~i" should be the same.
	
	Sample Code
	-----------
	
	  /*
	   * Compile options needed: none
	   */ 
	
	  #include <stdio.h>
	
	  main()
	  {
	     unsigned char i = 4;
	     unsigned char j = ~i;
	
	     if (j == ~i)
	        printf("passed\n");
	     else
	        printf("failed\n");
	  }
	
	The compiler performs the following four steps to evaluate the expression "if (j
	== ~i)":
	
	1. The compiler converts the operand "i" to an unsigned integer.
	
	2. The compiler complements the bits of this unsigned integer. On systems that
	  use 16-bit integers, the high byte becomes 0xFF; on systems that use 32-bit
	  integers, the three high bytes become 0xFFFFFF.
	
	3. The compiler converts the operand "j" to an unsigned integer. On systems that
	  use 16-bit integers, the high byte becomes 0x00; on systems that use 32-bit
	  integers, the three high bytes become 0x000000.
	
	4. The compiler compares the two operands.
	
	The comparison fails because the high bytes of the operands differ.
	
	To work around this situation, modify the comparison as follows:
	
	  if (j == (unsigned char)~i)
	
	Additional query words: 8.00 8.00c 9.00
	
	======================================================================
	Keywords          : kbCompiler kbVC100 kbVC150 kbVC200 kbVC400 kbVC500 kbVC600 
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : MS-DOS:6.0,6.00a,6.00ax,7.0; OS/2:6.0,6.00a; WINDOWS:1.0,1.5; WINDOWS NT:1.0,2.0,4.0,5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
