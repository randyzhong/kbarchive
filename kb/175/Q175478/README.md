---
layout: page
title: "Q175478: FS98: Flight Simulator Hangs During Setup"
permalink: /kb/175/Q175478/
---

## Q175478: FS98: Flight Simulator Hangs During Setup

{% raw %}

	Article: Q175478
	Product(s): Microsoft Home Games
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbenv kbsetup kbtlc fs98 kbimu msgamekbfaq
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Flight Simulator 98 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to install Microsoft Flight Simulator 98, more than one
	instance of the Setup program may start or Setup may stop responding (hang)
	before the installation is 40 percent complete. The most common behavior is a
	hang at 14 percent.
	
	CAUSE
	=====
	
	The CD-ROM drive may have a problem reading the Flight Simulator 98 compact
	disc. In an attempt to re-identify the compact disc, Microsoft Windows may start
	Flight Simulator Setup again.
	
	RESOLUTION
	==========
	
	The following steps should help resolve problems with reading the compact disc
	or help you to isolate the cause of the issue. Follow these steps in the order
	in which they are presented.
	
	1. Clean the compact disc. Focus on fingerprints, smudges, and dust. These can
	  often cause problems with reading the disc.
	
	   - Gently wipe the silver side of the disc with a soft, lint-free cotton
	     cloth. Do not use paper cloth, which may scratch the plastic or leave
	     streaks.
	
	   - Wipe from the center out. Do not use a circular motion.
	
	  After you clean the compact disc, attempt to run Setup again.
	
	2. Copy the following file from the Flight Simulator 98 CD-ROM
	
	  <drive>:\Fs98\Scenery\World\Scenery\South.bgl
	
	  where <drive> is the drive letter of your CD-ROM drive.
	
	  This file is the last file on the CD-ROM. If your drive is not able to read
	  this file, the drive may have physical limitations that prevent it from
	  reading the compact disc properly.
	
	  To copy this file from the Flight Simulator 98 CD-ROM, follow these steps:
	
	  a. Right-click an empty area on the desktop, point to New, and then click
	     Folder.
	
	  b. Insert the Flight Simulator 98 CD-ROM into your CD-ROM drive. Press and
	     hold down the SHIFT key as you insert the CD-ROM to prevent Flight
	     Simulator 98 from starting automatically.
	
	  c. Double-click My Computer.
	
	  d. Right-click the CD-ROM drive icon, and then click Explore.
	
	  e. Double-click the Fs98 folder.
	
	  f. Double-click the Scenery folder.
	
	  g. Double-click the World folder.
	
	  h. Double-click the Scenery folder.
	
	  i. Right-click the South.bgl file, and then click Copy.
	
	  j. Double-click the folder you created in Step A.
	
	  k. On the Edit menu, click Paste.
	
	3. If the issue continues to occur, turn off Auto Insert Notification. To do
	  this, follow these steps:
	
	  a. Click Start, point to Settings, and then click Control Panel.
	
	  b. Double-click System.
	
	  c. Click the Device Manager tab.
	
	  d. Click the PLUS SIGN (+) next to CDROM to expand the branch.
	
	  e. Click your CD-ROM drive, and then click Properties.
	
	  f. Click the Settings tab, and then click to clear the Auto Insert
	     Notification check box.
	
	  g. Click OK, and then click OK again.
	
	  h. Close Control Panel, and then restart the computer.
	
	  Run Flight Simulator Setup again. If the Setup program still seems to hang,
	  wait 5-10 minutes. The Setup program may seem to hang in several places, but
	  should complete successfully.
	
	4. If the issue continues to occur, change the supplemental cache size and
	  access pattern for the CD-ROM drive. To do this, follow these steps:
	
	  a. Click Start, point to Settings, and then click Control Panel.
	
	  b. Double-click System.
	
	  c. Click the Performance tab, and then click File System.
	
	  d. Click the CD-ROM tab.
	
	  e. Select one of the combinations of supplemental cache size and CD-ROM
	     access pattern listed in the following table.
	
	        Supplemental cache size   CD-ROM access pattern
	        ---------------------------------------------------
	
	        Large                     Actual CD-ROM Drive Speed
	        Large                     No Read-Ahead
	        Small                     No Read-Ahead
	        Small                     Actual CD-ROM Drive Speed
	
	     For example, move the Supplemental Cache Size slider to the Large position,
	     and then click the appropriate drive speed for your CD-ROM drive in the
	     Optimize Access Pattern For box. If your settings already match this
	     combination, use the next matching settings in the above table.
	
	  f. Click OK, and then click Close. When you are prompted to restart your
	     computer, click Yes.
	
	  g. If you could not copy the file in step 2, try copying it again. Otherwise,
	     run the Setup program again. If the issue continues to occur, repeat steps
	     A-F until you have tried all of the matching settings listed in step E.
	
	5. If you were able to copy the file in step 2, but still cannot run the Flight
	  Simulator Setup program, copy the following files and folders from the root
	  folder of the compact disc to a folder on your hard disk and install Flight
	  Simulator from that location.
	
	  NOTE: These instructions assume that you have already installed DirectX
	  version 5.0. Before you copy these files, make sure all files are visible. To
	  do this, follow these steps:
	
	  a. On the View menu in Windows Explorer, click Options.
	
	  b. On the View tab, click Show All Files.
	
	  c. Click OK.
	
	  Copy the files and folders in the following list from the root folder of the
	  Flight Simulator CD-ROM to a folder on your hard disk.
	
	   - Boosters
	   - FS98
	   - Indeo4
	   - Autorun.inf
	   - Dsetup.dll
	   - Dsetup16.dll
	   - Dsetup32.dll
	   - Mfc42.dll
	   - Msvcrt.dll
	   - Setup.exe
	   - Setupenu.dll
	
	  These folders and files require 415 megabytes (MB) of available hard disk
	  space.
	
	  IMPORTANT: If you cannot copy files from the CD-ROM to the hard disk, your
	  CD-ROM drive may be having problems reading the CD-ROM. Try copying the files
	  on another computer. If you cannot copy a specific file, try copying that
	  file on another computer. If the other computer is also unable to copy the
	  file, return the CD-ROM to your software vendor for a replacement package.
	
	  If the other computer can read the CD-ROM, then the disc itself is not
	  defective. Your CD-ROM drive may need to be cleaned. Microsoft suggests using
	  a commercially available CD-ROM lens-cleaning disc. These cleaning discs are
	  sold at computer and stereo stores, and are labeled for use with CD-ROM
	  drives and music CD players.
	
	  If you copy the files to the hard disk without error and are able to run the
	  Setup program to completion from the hard disk, a conflict may exist between
	  Flight Simulator 98 and your CD-ROM driver. Confirm that you are using the
	  latest 32-bit (protected mode) driver for your CD-ROM Drive.
	
	  For information about how to obtain the latest protected mode drivers for your
	  CD-ROM drive, contact your CD-ROM drive manufacturer. You can usually
	  download the latest drivers from the manufacturer's Web site.
	
	  To install Flight Simulator 98 from the hard disk, locate the Setup.exe file
	  you copied to your hard disk. For example, if you copied the Flight Simulator
	  files to a folder named Fltsim98 on your hard disk, locate that folder and
	  the double-click the Setup.exe file.
	
	  NOTE: If all files were not visible when you copied the files and folders from
	  the Flight Simulator CD-ROM, you receive the following error message when you
	  double-click the Setup.exe file:
	
	  Unable to load language specific dll. Unable to continue.
	
	  If you receive this error message, repeat steps A-C, and then copy the files
	  and folders again.
	
	If the installation completes successfully, you can delete the files and folders
	you copied to your hard disk. If you do this, you must specify the new location
	of the performance boosters.
	
	To specify the new location of the performance boosters, follow these steps:
	
	1. On the World menu, click Scenery Library.
	
	2. Click Performance.
	
	3. Under CD-ROM Performance Boosters, click the first scenery area in the list
	  of performance boosters and then click Edit.
	
	4. In the Source Path box, replace the hard disk letter with the CD-ROM drive
	  letter and then click OK. For example, if the CD-ROM drive letter is D, the
	  source path for FLTSIM98 CD-US Great Lakes should read:
	
	  D:\Boosters\USGL
	
	5. Repeat steps 3-4 for each scenery area in the performance boosters list.
	
	6. Click Restart.
	
	7. Click OK, and then click OK again to exit the scenery library.
	
	
	Additional query words: msgame fs98 flightsim fltsim many multiple copies
	
	======================================================================
	Keywords          : kbenv kbsetup kbtlc fs98 kbimu msgame kbfaq
	Technology        : kbGamesSearch kbFlightSimSearch kbFlightSim98 kbSimSearch
	Version           : WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
