---
layout: page
title: "Q137979: Creating Windows 9x Home Directories on Windows NT Server"
permalink: /kb/137/Q137979/
---

## Q137979: Creating Windows 9x Home Directories on Windows NT Server

{% raw %}

	Article: Q137979
	Product(s): Microsoft Windows NT
	Version(s): 2000,3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 05-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft Windows 95 
	- Microsoft Windows 98 
	- Microsoft Windows 98 Second Edition 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows 2000 Advanced Server 
	- Microsoft Windows 2000 Datacenter Server 
	- Microsoft Windows 2000 Professional 
	- Microsoft Windows 2000 Server 
	-------------------------------------------------------------------------------
	
	SYMPTOM
	=======
	
	Your Windows 95 clients cannot connect to their home directories even though you
	create a profile in Windows NT User Manager that specifies the Windows 95 users'
	home directory and drive letter to use for the connection.
	
	CAUSE
	=====
	
	Administrators cannot assign a home directory to Win 9x clients when they create
	users in User Manager. For Win9x, the home directory cannot be assigned in the
	user properties. This needs to be done in a logon script. The logon script can
	be run for all users but it simply fails for NT clients because their home
	directory is already assigned in user properties.
	
	RESOLUTION
	==========
	
	To allow Windows 95 users to connect to their home directories on the server,
	create a logon script to connect a Windows 95 client to a home directory and
	configure your Windows NT Primary Domain Controller (PDC) as follows:
	
	1. Create a test logon script on the Windows NT PDC for Windows 95 client
	  workstations:
	
	         echo on
	         net use * /HOME
	         pause
	
	2. Place the script file in the SYSTEM32\REPL\IMPORT\SCRIPTS directory on the
	  Windows NT PDC. (You may also want to set up File Replication so the logon
	  scripts you create are available on all domain controllers.)
	
	3. Make sure that the test user logging on has Full control of the \SCRIPTS
	  directory and at least Read permission on the Netlogon share (the default
	  share of \WINNT35\SYSTEM32\REPL\IMPORT\SCRIPTS).
	
	4. Create a subdirectory called TEST in the shared Users directory. By default
	  the shared Users directory is C:\USERS.
	
	5. 
	
	
	  Share the Test subdirectory with the share name TEST and give the test user
	  'Full Control' permission to the share.
	
	6. Run User Manager for Domains and select the user for the test.
	
	
	7. From the User menu, choose Properties.
	
	8. Choose Profile in the User Properties dialog box.
	
	9. Type the test logon script name in the Logon Script Name field.
	
	10. Under Home Directory, in the To field type:
	
	  \\<server_name>\TEST
	
	  NOTE: Ignore the drive letter in the Connect field.
	
	11. Log on as the test user at the Windows 95 client.
	
	  The following text appears at the command prompt:
	
	  c:\win95>echo on
	  c:\win95>net use * /home
	  d: connected to \\<servername>\TEST
	  c:\win95> pause
	  Press any key to continue. . .
	
	12. On the Windows 95 client, press any key to continue. Then doubleclick the My
	  Computer icon.
	
	  NOTE: In My Computer, the home directory maps to D: (or the next available
	  drive letter on the client).
	
	13. If the logon script executes correctly, you may delete the Echo On and pause
	  lines from your script resulting in your script consisting of only the
	  following line:
	
	  net use * /HOME
	
	NOTE: You may specify a drive letter in place of the Next Available Drive symbol,
	the star (*). You may also rename the Users\Test directory to any name; be sure
	to make the corresponding changes wherever this new directory name is used.
	
	MORE INFORMATION
	================
	
	Using NET USE * /HOME from Multiple MS-DOS Command Prompts
	----------------------------------------------------------
	
	If you use the NET USE * /HOME command from more than one MS-DOS command prompt
	in Windows 95, your current directory is going to be set incorrectly. Your
	current directory is going to be the root of the server containing your home
	directory instead of your default home directory.
	
	Additional query words: prodnt win95 win95x winnt
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000DataServ kbwin2000DataServSearch kbwin2000Serv kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbNTTermServ400 kbNTTermServSearch kbWinNTS351search kbWinNTS350search kbWin95search kbWin98search kbWin98SEsearch kbWinAdvServSearch kbWinDataServSearch kbZNotKeyword3 kbWin98 kbWin98SE
	Version           : :2000,3.5,3.51,4.0
	
	=============================================================================
	

{% endraw %}
