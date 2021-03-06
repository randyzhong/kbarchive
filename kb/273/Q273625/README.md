---
layout: page
title: "Q273625: Midtown Madness 2: How to Troubleshoot Video Problems"
permalink: /kb/273/Q273625/
---

## Q273625: Midtown Madness 2: How to Troubleshoot Video Problems

{% raw %}

	Article: Q273625
	Product(s): Microsoft Home Games
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbenv kbhw kbimu kbHardware
	Last Modified: 25-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Midtown Madness 2, version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to troubleshoot common video problems in Microsoft
	Midtown Madness 2.
	
	MORE INFORMATION
	================
	
	To troubleshoot video problems in Midtown Madness 2, restart the computer, and
	then use the following methods in the order in which they are presented.
	
	Check System Requirements
	-------------------------
	
	Make sure that your computer meets or exceeds the minimum system requirements
	that you need to run Midtown Madness 2.
	
	For additional information about the minimum system requirements that you need to
	run Midtown Madness 2, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q273786 Midtown Madness 2: Minimum System Requirements
	
	Reduce the Video Resolution and the Graphics Texture Quality
	------------------------------------------------------------
	
	To reduce the video resolution and the graphics texture quality in the game:
	
	1. Start Midtown Madness 2.
	
	2. On the startup screen, click Options.
	
	3. Click Graphics.
	
	4. In the Resolution box, click "640x480, 16 bit color".
	
	5. In the Texture Quality box, click Low - Recommended.
	
	6. In the Object Detail box, click Low.
	
	7. Click Done.
	
	8. Click Back.
	
	If the issue continues to occur, proceed to the next method.
	
	Turn Off Graphics Features
	--------------------------
	
	To turn off the graphics features in the game:
	
	1. On the main start screen, click Options.
	
	2. Click Graphics.
	
	3. Click to clear the following check boxes:
	
	   - Show Pedestrians
	   - Textured Sky
	   - Vehicle Reflections
	
	4. In the Cloud Shadows box, click None.
	
	If the issue continues to occur, proceed to the next method.
	
	Check for Known Video Configuration Issues
	------------------------------------------
	
	For additional information about how to check for known video configuration
	issues, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q273503 MM2: Known Video Issues in Midtown Madness 2
	
	If the issue continues to occur, proceed to the next method.
	
	Obtain and Install the Latest Version of Your Video Driver
	----------------------------------------------------------
	
	Contact your hardware manufacturer to inquire about how to obtain and install the
	latest version of the video driver for your video adapter.
	
	For information about how to contact your hardware manufacturer, click the
	appropriate article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	  Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	To determine the manufacturer and the model of the video adapter that is
	installed in your computer:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. Click the Device Manager tab.
	
	4. Click the plus sign (+) next to "Display adapters" to expand the branch.
	
	5. Under the Display Adapters branch, note the manufacturer and the model of
	  your video adapter, and then click OK.
	
	6. Close Control Panel.
	
	If the issue continues to occur, proceed to the next method.
	
	Disable 3D Hardware Acceleration in Midtown Madness 2
	-----------------------------------------------------
	
	To disable 3D hardware acceleration in Midtown Madness 2:
	
	1. Start Midtown Madness 2.
	
	2. On the main start screen, click Options.
	
	3. Click Graphics.
	
	4. In the Renderer box, click "Software only (no 3D video card)".
	
	5. Click Done.
	
	6. Click Back.
	
	If the issue continues to occur, proceed to the next method.
	
	Reduce Graphics Hardware Acceleration in Microsoft Windows
	----------------------------------------------------------
	
	To reduce graphics hardware acceleration in Windows:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. Click the Performance tab, and then click Graphics.
	
	4. Move the Hardware Acceleration slider until it is one notch to the right of
	  None (the Basic acceleration setting).
	
	5. Click OK, and then click Close.
	
	6. When you are prompted to restart the computer, click Yes.
	
	NOTE: If you encounter any problems after you reduce graphics hardware
	acceleration, follow these steps to restore graphics hardware acceleration to
	the original setting:
	
	  a. Restart Windows in Safe mode. To do this, follow the appropriate steps for
	     your operating system.
	
	     Microsoft Windows 98:
	
	     Restart your computer, press and hold down the CTRL key when your computer
	     completes the Power On Self Test (POST), and then select Safe Mode from
	     the Startup menu.
	
	     Microsoft Windows 95:
	
	     Restart the computer. When you see the "Starting Windows 95" message, press
	     the F8 key, and then select Safe Mode from the Startup menu.
	
	  b. When Windows starts in Safe mode, click OK.
	
	  c. Repeat steps 1 through 6, but in step 4 move the Hardware Acceleration
	     slider back to its original position.
	
	If the issue continues to occur, proceed to the next method.
	
	Use the Midtown Madness 2 Troubleshooting Shortcuts to Start the Game
	---------------------------------------------------------------------
	
	Double-click the Redetect Video icon.
	
	If the issue continues to occur, proceed to the next step.
	
	Double-click the Midtown 2 Safe Mode icon.
	
	For additional information about how to use the Midtown Madness 2 troubleshooting
	shortcuts, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q231828 Midtown 1.0/2.0: Description of the Troubleshooting Shortcuts
	
	If the issue continues to occur, proceed to the next method.
	
	Disable Mip Mapping
	-------------------
	
	To disable Mip Mapping:
	
	1. Right-click the Midtown Madness 2 icon on the desktop.
	
	2. Click Properties.
	
	3. Click the Shortcut tab.
	
	4. In the Target box, press the END key, press the SPACEBAR, and then type
	  "-nomipmap" (without the quotation marks).
	
	5. Click OK.
	
	6. Double-click the Midtown Madness 2 icon on the desktop.
	
	
	REFERENCES
	==========
	
	For additional information about how to troubleshoot issues in Midtown Madness
	2, click the article numbers below to view the articles in the Microsoft
	Knowledge Base:
	
	  Q273828 Midtown Madness 2: Game Sounds Are Not Played Correctly
	
	  Q273739 Midtown Madness 2: How to Improve Game Performance
	
	Additional query words: 2.00 msgame mm2 midmad sidewalk water display
	
	======================================================================
	Keywords          : kbenv kbhw kbimu kbHardware 
	Technology        : kbHomeProdSearch kbGamesSearch kbMidtownMadSearch kbMidtownMadness2
	Version           : :2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
