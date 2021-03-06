---
layout: page
title: "Q30419: ASSUME Directive Using SEG Operator on Structure Causes Error"
permalink: /kb/030/Q30419/
---

## Q30419: ASSUME Directive Using SEG Operator on Structure Causes Error

{% raw %}

	Article: Q30419
	Product(s): See article
	Version(s): 5.10
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | buglist5.10 | mspl13_masm
	Last Modified: 23-MAY-1988
	
	When the ASSUME directive uses the SEG operator, it causes an
	error.
	   The statement "cmp byte PTR fred.d1,0" in the following program
	incorrectly generates the "A2068: Cannot address with segment
	register" error message.
	   The program assembles correctly if the statement is modified to
	"cmp byte es:fred.d1,0."
	   Microsoft is researching this problem and will post new information
	as it becomes available.
	
	   The following program demonstrates the problem:
	
	   .MODEL LARGE,C
	
	   dog struc
	   d1  db  0
	   dog ends
	
	   .FARDATA
	   COMM fred:dog
	
	   .CODE
	   cat proc
	   assume es:SEG fred
	   cmp byte PTR fred.d1,0
	   ret
	   cat endp
	   end

{% endraw %}
