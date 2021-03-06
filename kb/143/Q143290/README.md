---
layout: page
title: "Q143290: PRB: Setting Menu Items to Grayed Does Not Disable the Item"
permalink: /kb/143/Q143290/
---

## Q143290: PRB: Setting Menu Items to Grayed Does Not Disable the Item

{% raw %}

	Article: Q143290
	Product(s): Microsoft C Compiler
	Version(s): winnt:2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbMenu kbMFC KbUIDesign kbVC150 kbVC200 kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 2.0, 2.1, 2.2, 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5, 1.51, 1.52 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you create a popup menu item and select its Grayed property in AppStudio, the
	menu item will appear Grayed in AppStudio and the GRAYED attribute will appear
	in the .RC file, but the menu item may not appear Grayed (disabled) when you run
	the application. The same behavior may appear for menus with the Inactive
	property.
	
	CAUSE
	=====
	
	CFrameWnd has a member variable name m_bAutoMenuEnabled, which is described in
	the Class Library reference. The documentation states that this variable is set
	to TRUE by default, meaning that any menu item that has an ON_COMMAND handler
	but no corresponding ON_UPDATE_COMMAND_UI handler will be automatically enabled.
	This variable overrides any setting you may have selected in your resource file.
	
	RESOLUTION
	==========
	
	If you would like to change this behavior, either implement the
	ON_UPDATE_COMMAND_UI handler or set the value of m_bAutoMenuEnabled to FALSE in
	the derived CFrameWnd constructor.
	
	STATUS
	======
	
	This behavior is by design.
	
	REFERENCES
	==========
	
	The Class Library Reference, documentation for ON_UPDATE_COMMAND_UI and
	CFrameWnd::m_bAutoMenuEnable.
	
	Additional query words: 1.00 1.50 2.50 2.51 2.52 2.00 2.10 2.20 3.00 3.10 3.20 4.00
	
	======================================================================
	Keywords          : kbMenu kbMFC KbUIDesign kbVC150 kbVC200 kbVC400 kbVC500 kbVC600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
