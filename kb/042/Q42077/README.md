---
layout: page
title: "Q42077: QuickC 2.00 README.DOC: Example Program PARRAY1.C"
permalink: /kb/042/Q42077/
---

## Q42077: QuickC 2.00 README.DOC: Example Program PARRAY1.C

{% raw %}

	Article: Q42077
	Product(s): See article
	Version(s): 2.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 2-MAY-1989
	
	The following information is taken from the QuickC Version 2.00
	README.DOC file, part 2, "Notes on 'C for Yourself.'" The following
	notes refer to specific pages in "C for Yourself."
	
	Page 110  Example Program PARRAY1.C
	
	Change the following line:
	
	   printf("array[%d]  = %d\n", count, *ptr++);
	
	to:
	
	   printf("i_array[%d] = %d\n", count, *ptr++);
	
	The PARRAY1.C program in on-line help already contains this
	correction, but you may want to correct the printed listing, too.

{% endraw %}
