---
layout: page
title: "Q45176: QB 4.50 On-Line Help Correction for UBOUND Statement"
permalink: /kb/045/Q45176/
---

## Q45176: QB 4.50 On-Line Help Correction for UBOUND Statement

{% raw %}

	Article: Q45176
	Product(s): See article
	Version(s): 4.50
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | SR# S890525-16 docerr | mspl13_basic
	Last Modified: 1-JUN-1989
	
	The QuickBASIC Version 4.50 on-line help utility contains a
	documentation error under the UBOUND statement. The incorrect sentence
	reads as follows:
	
	      UBOUND(array[,Dimension])
	
	   -- Dimension, an numeric-expression that has an integer value,
	      indicates the dimension of the array for which you want to see
	      the smallest available subscript.
	
	The sentence should be corrected to read as follows:
	
	      UBOUND(array[,Dimension])
	
	   -- Dimension, a numeric-expression that has an integer value,
	      indicates the dimension of the array for which you want to see
	      the largest available subscript.

{% endraw %}
