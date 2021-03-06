---
layout: page
title: "Q76727: FIX: MASM 5.1, 6.x, and the LOCK and REP Prefixes"
permalink: /kb/076/Q76727/
---

## Q76727: FIX: MASM 5.1, 6.x, and the LOCK and REP Prefixes

{% raw %}

	Article: Q76727
	Product(s): Microsoft Macro Assembler
	Version(s): MS-DOS:5.10,5.10a,6.0,6.0a,6.0b,6.1,6.10a,6.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 5.10, 5.10a, 6.0, 6.0a, 6.0b, 6.1, 6.10a, 6.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Macro Assembler (MASM) version 6.x will not assemble a statement
	with both a LOCK and a REP prefix. MASM 6.x generates the following error
	message:
	
	  error A2008: syntax error : rep
	
	MASM versions 5.1 and 5.1a will assemble without error, however, code that uses
	the LOCK prefix with an incorrect instruction, but the code generated will run
	without errors only on some machines.
	
	CAUSE
	=====
	
	The validity of using LOCK with REP depends upon the processor on which the
	program is to be executed. A LOCK REP instruction is allowed on 186 processors
	and is even required in certain cases. However, on 386, 486, and the Pentium
	processors, the LOCK REP instruction will generate an invalid opcode exception.
	
	For the 80186 processor, LOCK REP MOVS and LOCK REP OUTS are valid instructions
	and are required in some cases, especially to work with the peripheral control
	block (PCB) registers.
	
	For the 80286 and higher processors, the LOCK prefix is valid only with the
	following instructions and only when they modify memory:
	
	  BTS, BTR, BTC -> bit test and change instructions
	  XCHG, XADD, CMPXCHG -> exchange instructions
	  INC, DEC, NOT, NEG -> single operand instructions
	  ADD, ADC, SUB, SBB, AND, OR, XOR -> two operand arithmetic and logic
	
	An invalid opcode exception results from using the LOCK prefix before any other
	instruction, or with these instructions that do not modify memory (that is, if
	the destination is a register).
	
	Because of the danger of allowing improper use of the LOCK instruction, MASM 6.x
	does not allow it to be used with the REP prefix even though the Intel 80186
	manual specifically calls for such use in certain circumstances. Programmers
	developing embedded applications using the 80186 series may need this
	capability, however, and the sample code shows a technique for doing this. In
	these cases, the programmer will need to be certain that the code will never be
	run on a CPU where it could cause errors.
	
	STATUS
	======
	
	Microsoft has confirmed that allowing LOCK to be assembled for invalid
	instructions is a problem in MASM versions 5.1 and 5.1a. This problem was
	corrected in MASM version 6.0, and by design is not allowed to be used with the
	REP prefixes.
	
	RESOLUTION
	==========
	
	When programming for the 80186 processor using MASM 6.x, a byte can be inserted
	into the program that contains 0F0h, the prefix for LOCK. The sample code below
	demonstrates this solution. Macros can be used to make this an easier
	workaround.
	
	MORE INFORMATION
	================
	
	Sample Code
	-----------
	
	  ; Assemble options needed: /c
	  .MODEL small
	  .186
	  .DATA
	  astr    DB    "Hello, world.", 13, 10, 0
	  msg     DB    16 DUP(?)
	
	  .CODE
	  proc1   PROC
	          mov     cx, 10h                 ; Load the SI, DI, and CX
	          mov     si, OFFSET astr         ;  registers and clear the
	          mov     di, OFFSET msg          ;  direction flag for the
	          cld                             ;  string transfer.
	
	  ;       DB      0F0h                    ; Uncomment this line and
	                                          ;  remove the LOCK prefix on
	                                          ;  the following instruction
	                                          ;  to work around the problem
	          lock rep movsb                  ; This line does not assemble
	                                          ; in MASM 6.x.
	  ENDP    proc1
	  END
	
	REFERENCES
	==========
	
	
	Intel iAPX 86/88, 186/188 User[ASCII 146]s Manual Programmer[ASCII 146]s
	Reference.
	
	Intel 386 DX Microprocessor Programmer[ASCII 146]s Reference manual.
	
	Also see the Intel manuals for the 486, Pentium, and newer 186 CPUs. Manuals are
	available directly from Intel Corporation at the following address:
	
	  Intel Literature Sales
	  P.O. Box 7641
	  Mt. Prospect, IL 60056-7641
	  phone: 800-548-4725
	
	Additional query words: 5.10 5.10a 6.00 6.00a 6.00b 6.10 6.10a buglist5.10 buglist5.10a fixlist6.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM600 kbMASM610 kbMASM611 kbMASM600a kbMASM600b
	Version           : MS-DOS:5.10,5.10a,6.0,6.0a,6.0b,6.1,6.10a,6.11
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
