---
layout: page
title: "Q304999: How to Replace Missing System and TrueType Fonts"
permalink: /kb/304/Q304999/
---

## Q304999: How to Replace Missing System and TrueType Fonts

{% raw %}

	Article: Q304999
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbenv kbtool
	Last Modified: 17-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to replace missing system and TrueType fonts. This
	may be useful in a situation where system or TrueType fonts are missing, and you
	want to replace them but you do not want to run a repair installation of the
	operating system.
	
	MORE INFORMATION
	================
	
	NOTE: The Windows NT 4.0 CD-ROM is required to install system fonts. To install
	TrueType fonts you can use either the Windows NT 4.0 CD-ROM or a network share
	to the Fonts folder on another Windows NT-based computer.
	
	To replace missing system and TrueType fonts:
	
	1. Create a folder that is named "Fonts" (without the quotation marks) on drive
	  C.
	
	2. At a command prompt, change to the i386 folder on the Windows NT 4.0 CD-ROM.
	
	3. Use the "expand" (without the quotation marks) command to expand the fonts
	  from the CD-ROM into the Fonts folder by running the "expand -r *.fo_
	  c:\fonts" (without the quotation marks) command. To expand TrueType fonts,
	  use the "expand -r *.tt_ c:\fonts" (without the quotation marks) command. You
	  can also install TrueType fonts from another computer across the network, by
	  using a mapped network drive to connect to the Fonts folder on another
	  computer.
	
	4. In Windows NT Explorer, click the c:\WINNT\Fonts folder, and then click
	  Install New Font on the File menu.
	
	5. Open the c:\Fonts folder, and then double click this folder to load the font
	  list. After the fonts are discovered by the Add Fonts tool, choose the font
	  or fonts you want to install, and then click OK.
	
	  The fonts should now be successfully installed. It may appear that duplicate
	  fonts are in the Fonts folder, however, only one instance of the font appears
	  in programs where you can choose fonts.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbtool 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
