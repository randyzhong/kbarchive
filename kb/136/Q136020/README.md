---
layout: page
title: "Q136020: INFO: Glyphs in Visual C++ with Source Code Control Enabled"
permalink: /kb/136/Q136020/
---

## Q136020: INFO: Glyphs in Visual C++ with Source Code Control Enabled

{% raw %}

	Article: Q136020
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kbSSafe400 kbSSafe500 kbSSafe600 kbVC400 kbVC500 kbVC600
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 4.0, 5.0, 6.0 
	- Microsoft Visual C++, version 4.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Visual C++ supports integration with a source code control provider, such as
	Visual SourceSafe. The color and glyphs used in File View reflect the state of
	any given file within a project workspace relative to source code control.
	
	The information in this article is valid independent of the source code control
	provider you use, but is specific to Visual SourceSafe.
	
	MORE INFORMATION
	================
	
	In FileView, if a given file is under source code control, the "file glyph" is
	one sheet of gray paper, folded in the right corner. If the file is not under
	source code control, the file glyph is one sheet of white paper, folded in the
	right corner. If the file is under source code control and is shared with
	another project, the file glyph is two sheets of gray paper folded in the right
	corner. Files checked out from the source code control provider have a red check
	mark to the left of the file glyph.
	
	It is possible to create a resource script and check it out, but not check out
	underlying image files used by the resource script. Developer Studio is smart
	enough to prompt you to check out, for example, the underlying .bmp file before
	allowing you to start editing a toolbar bitmap. If you do not check the file
	out, you will not be able to save any changes you make to the bitmap file.
	
	NOTE: For non-text files, only one user can effectively check the file out at a
	time.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400 kbSSafe500 kbSSafe600 kbVC400 kbVC500 kbVC600 
	Technology        : kbVCsearch kbVC400 kbSSafeSearch kbAudDeveloper kbVC500 kbVC600 kbVC32bitSearch kbSSafe600 kbSSafe400 kbSSafe500 kbVC500Search
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
