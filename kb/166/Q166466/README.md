---
layout: page
title: "Q166466: Err Msg: Setup Found a Compressed Volume or a Disk-Cache Utility"
permalink: /kb/166/Q166466/
---

## Q166466: Err Msg: Setup Found a Compressed Volume or a Disk-Cache Utility

{% raw %}

	Article: Q166466
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 1,2,2.1
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup osr1 osr2 win95
	Last Modified: 02-FEB-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 95 OEM Service Release, versions 1, 2, 2.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you run Setup for the retail (non-OSR2) version of Windows 95 and try to
	install Windows 95 in a folder containing an OEM Service Release version of
	Windows 95, you may receive the following error message:
	
	  Windows Setup
	  Setup found a compressed volume or a disk-cache utility on your computer. Quit
	  setup and check your compressed volume with your disk- compression software
	  or remove the disk-cache utility. Then run Setup again.
	
	This error message can also occur if you start your computer using a Microsoft
	Windows 98 Startup disk, enable CD-ROM support, and then attempt to install
	Windows 95.
	
	If you continue trying to install Windows 95 on a hard disk using the FAT32 file
	system, you may receive error message "SU-0013."
	
	If you are installing Windows 95 on a hard disk using the FAT16 file system,
	Setup continues but experiences numerous file version conflicts that generate
	the following message:
	
	  A file being copied is older than the file currently on your computer.
	  It is recommended that you keep your existing file.
	
	If you click Yes to keep the newer files, Setup finishes, but when you restart
	the computer you may experience any of the following symptoms:
	
	- The computer stops responding (hangs) at the logo screen.
	
	- You receive the error message "Fatal Exception 0D has occurred at
	  0117:00007E1F."
	
	Starting Windows 95 in Safe mode may generate the following error message:
	
	  Fatal Exception 0D has occurred at 0117:00007E1F.
	
	CAUSE
	=====
	
	The version of Windows 95 being installed is not the same version that is
	already installed.
	
	To verify the version you are installing, type "ver" at a command prompt. Version
	4.00.950 (files dated 7-11-95)is retail and OEM (non-OSR2). Version 4.00.1111
	(files dated 8-24-96) indicates Windows 95 OEM Service Release 2 (OSR2).
	
	RESOLUTION
	==========
	
	Do not install the retail or OEM (non-OSR2) version of Windows 95 into an
	existing Windows 95 OSR2 folder. If you are installing to a hard disk using the
	FAT16 file system, install to a different folder. Do not install the retail or
	OEM (non-OSR2) version of Windows 95 on a hard disk using the FAT32 file system.
	
	MORE INFORMATION
	================
	
	When you attempt to install the retail version of Windows 95 from the Windows 95
	CD-ROM on a computer with OSR2 installed with the Auto Insert Notification
	option enabled, the Add/Remove Software option on the Autorun menu is disabled.
	You receive the following warning:
	
	  This CD-ROM is from an older version of Windows than the one you are
	  presently using. Setup functionality from this disk will be disabled.
	
	A warning does not appear if:
	
	- You are installing from a CD-ROM but the Auto Insert Notification option is
	  disabled.
	
	- You browse the Windows 95 CD-ROM and you double-click Setup.exe.
	
	- You run Setup from the Run dialog box.
	
	You should reinstall OSR2 using the OSR2 CD-ROM provided by your OEM. If an OSR2
	CD-ROM was not provided to you by your OEM, the OSR2 files may have been
	provided in a flat folder on your hard disk. To locate this folder, type the
	following command at a command prompt:
	
	  "dir *.cab /s" (without the quotation marks)
	
	To reinstall OSR2, run Setup.exe from the folder containing the OSR2 cabinet
	(.cab) files.
	
	Contact your OEM for assistance if:
	
	- You do not have an OSR2 CD-ROM and you cannot locate a folder with the
	  cabinet files.
	
	- You cannot locate the Setup.exe file in the folder that contains the cabinet
	  files.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbsetup osr1 osr2 win95 
	Technology        : kbWin95search kbOPKSearch kbZNotKeyword3 kbWin95OPKOSR2 kbWin95OPKOSR1 kbWin95OPKOSR210
	Version           : :1,2,2.1
	
	=============================================================================
	

{% endraw %}
