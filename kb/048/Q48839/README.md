---
layout: page
title: "Q48839: Warning L4014: /PACKDATA: Option Ignored for Real Mode"
permalink: /kb/048/Q48839/
---

## Q48839: Warning L4014: /PACKDATA: Option Ignored for Real Mode

{% raw %}

	Article: Q48839
	Product(s): See article
	Version(s): 4.06 4.07 5.02 5.03 | 5.02 5.03
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 21-SEP-1989
	
	/PACKDATA is incorrectly listed as an available switch for LINK
	Versions 4.06 and 4.07. LINK Version 4.06 comes with the QuickC
	compiler, and LINK Version 4.07 comes with the QuickAssembler.
	
	The /PACKDATA option is valid ONLY for segmented-executable files --
	OS/2 or Windows; it has no meaning for DOS. Real mode executable means
	a DOS-only program. To use the /PACKDATA switch, create a .DEF file
	with at least the following statement:
	
	   NAME    MyProtectModeProgram
	
	This switch is implemented in segmented-executable LINK Versions 5.02
	and later.

{% endraw %}
