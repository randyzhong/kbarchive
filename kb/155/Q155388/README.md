---
layout: page
title: "Q155388: PRB: CLEAR RESOURCE Does Not Appear to Work"
permalink: /kb/155/Q155388/
---

## Q155388: PRB: CLEAR RESOURCE Does Not Appear to Work

{% raw %}

	Article: Q155388
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbvfp500 kbvfp600
	Last Modified: 14-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The CLEAR RESOURCES command, a new command for Visual FoxPro 5.0, does not
	appear to work. When Visual FoxPro displays a bitmap, picture, cursor, icon, or
	font resource, Visual FoxPro caches the resource to optimize performance. If you
	use a resource of the same name (for example, a different bitmap with the same
	name as the one already cached), Visual FoxPro does not reload the resource.
	
	Therefore, clearing a resource file is useful for removing a graphic image from
	memory and forcing Visual FoxPro to reload an image of the same name from disk.
	For example, a report might display graphic images from a database, all of which
	are named TEMP; however, because they all have the same name, Visual FoxPro does
	not reload each new graphic unless the existing one has been cleared from memory
	using the CLEAR RESOURCES command.
	
	CAUSE
	=====
	
	This scenario occurs when a resource is in use when you issue the CLEAR
	RESOURCES command.
	
	RESOLUTION
	==========
	
	The CLEAR RESOURCES command acts only on resources that are not currently in
	use. In the following example, the "Toggle bitmap" button attempts to clear a
	resource that is in use. The click code for the "Update form" button saves the
	current value of the picture property, sets the picture property to "", clears
	the resource (which is no longer in use), and resets the picture property back
	to its original value. Note that the specific resource is cleared by name. Any
	remaining resources are not cleared. The resources must be cleared because of
	caching for performance reasons. You want to clear only the resource you want to
	update so that any others will still be in the cache.
	
	STATUS
	======
	
	This behavior is by design. CLEAR RESOURCES acts only on resources not currently
	in use.
	
	MORE INFORMATION
	================
	
	1. Run the following code from a .prg:
	
	        PUBLIC oform
	        oform=CREATEOBJECT('form1')
	        oform.Show
	
	        DEFINE Class form1 AS Form
	          Top = 0
	          Left = 0
	          Height = 234
	          Width = 207
	          DoCreate = .T.
	          Caption = "Clear Resource Demo"
	          Name = "form1"
	          changedbmp = .F.
	          ADD OBJECT image1 AS Image WITH ;
	            Stretch = 2, ;
	            Height = 120, ;
	            Left = 36, ;
	            Top = 12, ;
	            Width = 144, ;
	            Name = "Image1"
	          ADD OBJECT command1 AS CommandButton WITH ;
	            Top = 156, ;
	            Left = 60, ;
	            Height = 27, ;
	            Width = 96, ;
	            Caption = "\<Toggle bitmap", ;
	            Default = .T., ;
	            Name = "Command1"
	         ADD OBJECT command2 AS CommandButton WITH ;
	            Top = 192, ;
	            Left = 67, ;
	            Height = 27, ;
	            Width = 84, ;
	            Caption = "\<Update form", ;
	            Name = "Command2"
	
	          PROCEDURE image1.Init
	            Clear RESOURCES
	            COPY FILE home()+'wizards\wizbmps\wzclose.bmp' TO 'bmptemp.bmp'
	            THIS.Picture='bmptemp.bmp'
	          ENDPROC
	
	          PROCEDURE command1.Click
	            IF THISFORM.changedbmp=.F.
	              THISFORM.changedbmp=.T.
	              COPY FILE home()+'wizards\wizbmps\wzedit.bmp' TO 'bmptemp.bmp'
	            ELSE
	              THISFORM.changedbmp=.F.
	              COPY FILE home()+'wizards\wizbmps\wzclose.bmp' TO 'bmptemp.bmp'
	            ENDIF
	            CLEAR RESOURCES
	            THISFORM.REFRESH
	          ENDPROC
	
	          PROCEDURE command2.Click
	            LOCAL lcPictemp
	            lcPictemp=thisform.image1.Picture
	            THISFORM.image1.Picture=''
	            CLEAR RESOURCES (lcPictemp)
	            THISFORM.image1.Picture=lcPictemp
	          ENDPROC
	  ENDDEFINE
	
	2. Press the "Toggle bitmap" button. Note how the button does not update the
	  image even though it contains a CLEAR RESOURCES command in its click code.
	
	3. Press the "Update form" button. Now the image is updated.
	
	REFERENCES
	==========
	
	Visual FoxPro Help file.
	
	Additional query words: kbdse Vfoxwin
	
	======================================================================
	Keywords          : kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	
	=============================================================================
	

{% endraw %}
