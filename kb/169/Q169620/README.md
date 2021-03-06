---
layout: page
title: "Q169620: Err Msg: Accessing CD-ROM Drive: D:&#92; Is Not Accessible"
permalink: /kb/169/Q169620/
---

## Q169620: Err Msg: Accessing CD-ROM Drive: D:&#92; Is Not Accessible

{% raw %}

	Article: Q169620
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbhw kbsetup kbHardware
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Windows NT is installed using WINNT /B on a computer using either EIDE
	controllers and IDE drives, or a SCSI controller and IDE or SCSI drives, without
	an attached IDE CD-ROM drive. At a later time, an ATAPI 1.2- compliant IDE
	CD-ROM drive is attached to the system, and Windows NT recognizes the CD-ROM
	drive in both Disk Administrator and Windows Explorer with an assigned drive
	letter. When the user tries to access the CD-ROM drive using Windows Explorer,
	the user receives one of two error messages:
	
	  D:\ is not accessible.
	
	  The volume does not contain a recognized file system. Please make sure that
	  all required file system drivers are loaded and that the volume is not
	  corrupt.
	
	-or-
	
	From a Windows NT MS-DOS command prompt:
	
	  The System cannot find the drive specified.
	
	
	CAUSE
	=====
	
	This problem occurs because the CD-ROM file system (CDFS) registry entries are
	not properly initialized during Setup when a CD-ROM drive is not attached.
	
	RESOLUTION
	==========
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Go to
	
	     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\Root
	     \Legacy_Cdrom\0000.
	
	3. On the Registry menu, click Save key and call it 000.reg.
	
	4. Go to
	
	     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum
	        \Root\Legacy_Cdfs\0000.
	
	5. Click the 0000 key, and then click Permissions on the Security menu.
	
	6. Change the 0000 key permissions to Everyone : Full Control, and then click
	  OK.
	
	7. On the Registry menu, click Restore, and restore the 000.reg key saved from
	  step 3 on top of the current 0000 key under Legacy_cdfs.
	
	8. Under the restored 000 key, modify the following two entries:
	
	  a. Change DeviceDesc:REG_SZ:Cdrom Device to Cdfs Device.
	
	  b. Change Service:REG_SZ:Cdrom to Cdfs.
	
	9. Exit Regedt32.exe and then restart Windows NT. The CD-ROM drive should now
	  work normally.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0. We are
	researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	======================================================================
	Keywords          : kbhw kbsetup kbHardware 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
