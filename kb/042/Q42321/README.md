---
layout: page
title: "Q42321: Syntax Error, Duplicate Definition, Expected:Variable=Express"
permalink: /kb/042/Q42321/
---

## Q42321: Syntax Error, Duplicate Definition, Expected:Variable=Express

{% raw %}

	Article: Q42321
	Product(s): See article
	Version(s): 4.00 4.00b 4.50
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | SR# S890209-84 B_BasicCom | mspl13_basic
	Last Modified: 12-DEC-1989
	
	The sample code below shows three very closely related pairs of BASIC
	code. Each example produces a different error, as shown.
	
	This information applies to the QB.EXE environment supplied with
	QuickBASIC Versions 4.00, 4.00b, and 4.50, Microsoft BASIC Compiler
	Versions 6.00 and 6.00b for MS-DOS, and the QBX.EXE environment
	supplied with Microsoft BASIC PDS Version 7.00 for MS-DOS.
	
	Under QuickBASIC Version 3.00, all three code segments produce the
	error message "MISSING =".
	
	The following are code examples:
	
	' PROG #1
	     bd% = 6
	     bd% - 13 = c   ' "Expected: variable= expression"
	
	' PROG #2
	     bd% = 6        ' "Duplicate Definition"
	     bd - 13 = c
	
	' PROG #3
	     x% = 6
	     bd - 13 = c    ' "Syntax error"

{% endraw %}
