---
layout: page
title: "Q137821: Removing Desktop Themes May Remove Fonts"
permalink: /kb/137/Q137821/
---

## Q137821: Removing Desktop Themes May Remove Fonts

{% raw %}

	Article: Q137821
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 18-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Plus! for Windows 95 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you remove a Microsoft Plus! for Windows 95 desktop theme, you may find that
	fonts installed by a Microsoft Font Pack or Microsoft Office are missing from
	your system.
	
	CAUSE
	=====
	
	When you remove a desktop theme, all the associated files are removed. These
	associated files can include sounds, pointers, and fonts (even if the fonts were
	originally installed by a different program).
	
	RESOLUTION
	==========
	
	To work around this problem, use either of the following methods:
	
	- Before you remove a desktop theme, move or rename the font in the
	  Windows\Fonts folder. After you remove the desktop theme, move or rename the
	  font to its original name or location.
	
	- Reinstall the missing font from the program that originally installed it.
	
	MORE INFORMATION
	================
	
	The following desktop themes use the following fonts:
	
	Theme                         Font
	----------------------------------
	Dangerous Creatures           Arial
	Inside your Computer          Abadi MT Condensed Light
	Leonardo da Vinci             Book Antiqua
	Flying Windows                News Gothic MT
	Mystery                       Calisto MT
	Nature                        Copperplate Gothic Light
	Science                       Lucida Sans Unicode
	Sports                        OCR A Extended
	The 60's USA                  Lucida Handwriting
	The Golden Era                Century Gothic
	Travel                        Comic Sans MS
	Windows 95                    News Gothic MT
	
	Additional query words: uninstall
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbGamesSearch kbPlusSearch kbZNotKeyword3 kbPlus95
	Version           : 95
	
	=============================================================================
	

{% endraw %}
