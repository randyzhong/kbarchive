---
layout: page
title: "Q102432: FIX: Incorrect RET Generated for PROC when EPILOGUE:NONE"
permalink: /kb/102/Q102432/
---

## Q102432: FIX: Incorrect RET Generated for PROC when EPILOGUE:NONE

{% raw %}

	Article: Q102432
	Product(s): Microsoft Macro Assembler
	Version(s): 6.0,6.0a,6.0b,6.1,6.1a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 6.0, 6.0a, 6.0b, 6.1, 6.1a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When Microsoft Macro Assembler (MASM) processes source code for an application,
	it may generate the incorrect form for a RET instruction in a PROC.
	Specifically, the assembler generates a RET 4 instruction instead of a RET
	instruction when the source code contains a RET instruction.
	
	CAUSE
	=====
	
	The source code uses the OPTION EPILOGUE statement multiple times to set the
	EPILOGUE macro to NONE.
	
	RESOLUTION
	==========
	
	Modify the source code to specify RET 0. The assembler translates this
	expression into a RET instruction.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in MASM versions 6.0, 6.0a, 6.0b,
	6.1, and 6.1a. This problem was corrected in MASM for MS-DOS version 6.11.
	
	MORE INFORMATION
	================
	
	The following code example demonstrates this problem:
	
	Sample Code
	-----------
	
	  ; Assembler options needed: /c /Fl /Sa
	
	  .MODEL small, Pascal
	
	  _text SEGMENT
	
	  OPTION EPILOGUE:NONE
	  p0 PROC parm1:DWORD
	      ret                 ; This correctly generates a RET
	  p0 ENDP
	
	  OPTION EPILOGUE:EpilogueDef
	  p1 PROC parm1:DWORD
	      ret                 ; This correctly generates a RET 4
	  p1 ENDP
	
	  OPTION EPILOGUE:NONE
	  p2 PROC parm1:DWORD
	      ret                 ; This incorrectly generates a RET 4
	  p2 ENDP
	
	  _text ENDS
	
	  END
	
	Additional query words: 6.00 6.00a 6.00b 6.10 6.10a buglist6.00a buglist6.00b buglist6.10 buglist6.10a fixlist6.11
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM600 kbMASM610 kbMASM610a kbMASM600a kbMASM600b
	Version           : :6.0,6.0a,6.0b,6.1,6.1a
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
