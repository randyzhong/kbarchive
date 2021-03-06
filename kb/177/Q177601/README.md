---
layout: page
title: "Q177601: Microsoft File and Print Services for NetWare Readme.txt"
permalink: /kb/177/Q177601/
---

## Q177601: Microsoft File and Print Services for NetWare Readme.txt

{% raw %}

	Article: Q177601
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbinterop
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft File and Print Services for NetWare version 4.0 
	-------------------------------------------------------------------------------
	
	The following is the text of the Microsoft File and Print Services for
	NetWare (FPNW) version 4.0 Readme.txt file.
	
	Microsoft File and Print Services for NetWare for Microsoft Windows NT
	Server Version 4.0
	-----------------------------------------------------------------------------------------
	
	Release Note:
	
	Welcome to File and Print Services for NetWare (FPNW) for Microsoft Windows
	NT Server version 4.0. This compact disc contains both File and Print
	Services for NetWare and Directory Service Manager for NetWare.
	
	Installing FPNW Version 4.0:
	
	File and Print Services for NetWare version 4.0 can be installed only on
	computers running Windows NT Server version 4.0. You must be logged on as a
	member of the Administrators group to install FPNW.
	
	Follow this procedure only to install FPNW version 4.0 on a computer that
	does not already have FPNW. To upgrade from a previous version of FPNW ,
	see "Upgrading From Previous Version of FPNW."
	
	To Install FPNW:
	
	1. Insert the Services for NetWare compact disc in the computer's CD-ROM drive.
	
	2. Double-click My Computer, and then double-click Control Panel.
	
	3. Double-click Network.
	
	4. Click the Services tab, then click Add.
	
	5. Click Have Disk. IMPORTANT -- If File and Print Services for NetWare appears
	  in the Network Service list, do not select it; instead, click "Have Disk".
	
	6. Type the appropriate path, and click OK.
	
	  The path is drive:\FPNW\NT40\processor, where drive is the drive letter of the
	  CD-ROM drive and processor is the server's processor type. For example, type
	  d:\fpnw\nt40\i386 to install on an x86-based computer with a CD-ROM drive at
	  drive D. The possible values for processor are i386, MIPS, ALPHA, and PPC.
	
	7. Select File and Print Services for NetWare, and click OK. The Setup program
	  copies files.
	
	8. In the Directory For SYS Volume box, type the location for the SYSVOL
	  directory that will be the NetWare SYS: volume. It is recommended that you
	  specify a directory on an NTFS partition; if you specify a directory on a
	  non-NTFS partition, you lose the security features that NTFS provides and
	  will not be able to set or enforce file or directory security settings.
	
	9. In the Server Name box, type the computer name that NetWare client computers
	  will use to access the server. The default is the server's computer name with
	  _FPNW (underscore FPNW) appended.
	
	  IMPORTANT -- The Server Name you specify must be in all capital letters and
	  must be unique.
	
	10. Type a password for the Supervisor's account in the Supervisor Account group
	  box.
	
	  You must type the same password in the Password and Confirm Password boxes.
	  The password can be as many as 14 characters, and is case- sensitive.
	
	11. In the Advanced Tuning group box, select one of the options to tune the
	  server's performance.
	
	  You can change these options later using the Network application in the
	  Control Panel. Click the Services tab, click "File and Print Services for
	  NetWare," and then click Properties.
	
	12. If you are installing File and Print Services for NetWare on a domain
	  controller, you are prompted to enter a password for the FPNW Service
	  Account.
	
	  If you install File and Print Services for NetWare on multiple domain
	  controllers in a domain, you must specify the same password for this account
	  on each domain controller on which you install the utility.
	
	13. Click Close, and then restart the computer to complete the installation.
	
	Upgrading From a Previous Version of FPNW
	-----------------------------------------
	
	Follow this procedure only to upgrade to version 4.0 of FPNW on a server
	that already has FPNW version 3.51 or an earlier beta of FPNW version 4.0
	installed.
	
	IMPORTANT -- Do not run any previous versions of FPNW on a server running
	Windows NT Server 4.0. Use the following steps to upgrade a server from
	version 3.51 of Windows NT Server and FPNW to the 4.0 versions of these
	products:
	
	1. Stop the File and Print Services for NetWare service on the server. To do so,
	  use the Services icon in Control Panel, or type net stop fpnw.
	
	2. Upgrade Windows NT Server to version 4.0. For instructions, see your Windows
	  NT Server documentation.
	
	3. Upgrade File and Print Services for NetWare to version 4.0. For instructions,
	  see the following procedure.
	
	To Upgrade to FPNW Version 4.0
	------------------------------
	
	1. Insert the Services for NetWare compact disc in the computer's CD-ROM drive.
	
	2. Double-click My Computer, then double-click Control Panel.
	
	3. Double-click Network.
	
	4. Click the Services tab.
	
	5. Select File and Print Services for NetWare, then click Update.
	
	6. Type the appropriate path, and click OK.
	
	  The path is drive:\FPNW\NT40\processor, where drive is the drive letter of the
	  CD-ROM drive and processor is the server's processor type.
	
	  For example, type d:\fpnw\nt40\i386 to install on an x86-based computer with a
	  CD-ROM drive at drive D. The possible values for processor are i386, MIPS,
	  ALPHA, and PPC.
	
	7. Click Close, and then restart the computer to complete the installation.
	
	INSTALLING NOTE
	---------------
	
	Installation Problem With Alpha Processors
	
	If you install on a computer with an Alpha processor, using the computer's
	own CD-ROM drive, you may receive the following error message during file
	copying:
	
	  An error occurred while Windows was working with the Control Panel file
	  %systemroot%\system32\ncpa.cpl
	
	To work around the problem, put the Services for NetWare compact disc in
	another computer's CD-ROM drive, share the drive, and install using the
	remote CD-ROM drive.
	
	Online Administrator's Guide
	----------------------------
	
	Services for NetWare includes an online Administrator's Guide. To install
	the online Administrator's Guide on your computer, copy all the files from
	the \FPNW\NT40\ONLINE.DOC directory of the compact disc to a directory on
	the hard drive.
	
	To use the online book, double-click the MS-SFN.HLP file icon in the
	Explorer, or specify that file in the Run command of the Start menu.
	
	Remote Administration Tools for Windows 95 and Windows for Workgroups:
	
	This compact disc also contains remote administration tools, which can be
	used to administer Windows NT Server from computers running Windows 95 and
	Windows for Workgroups.
	
	The tools in the \WIN95.RAD directory are for use on Windows 95 computers.
	These tools include functionality to remotely administer File and Print
	Services for NetWare, as well as Windows NT Server. For more information On
	these tools, see \WIN95.RAD\SRVTOOLS.TXT, or see the online help by Typing
	win32hlp d:\win95.rad\srvtools.hlp, where d: is the drive letter of the CD-
	ROM.
	
	The tools in the \WFW.RAD directory are for use on Windows for Workgroups
	computers. These tools include functionality to remotely administer only
	Windows NT Server. For more information on these tools, see
	\WFW95.RAD\Readme.txt.
	
	IMPORTANT -- Do not use previously released versions of these remote
	administration tools to administer FPNW (NetWare-enabled ) users. These
	previous versions may corrupt the user account information of FPNW users.
	
	If you are using Windows NT Server remote administration tools on any
	Windows 95 or Windows for Workgroups computers, update them to the versions
	contained on this compact disc immediately.
	
	Miscellaneous Notes
	-------------------
	
	Removing FPNW:
	
	After you remove FPNW and reboot, the FPNW control panel application will
	still be present. To remove the application, close the control panel, and
	then delete the %systemroot%\system32\fpnwmgr.cpl file.
	
	Incorrect Installation of Earlier FPNW Beta on Windows NT Server 4.0 RC:
	
	If you upgraded to Windows NT Server 4.0 RC, and then tried installing an
	earlier Beta version of FPNW 4.0, you have an incorrect version of
	fpnwclnt.dll installed. To expand and copy the correct version from the
	Services for NetWare compact disc, type
	
	"expand  d:\fpnw\nt40\i386\fpnwclnt.dl_ %systemroot%\system32\fpnwclnt.dll" (without the quotation marks)
	
	where d: is the CD-ROM drive.
	
	NetWare Client 32TM Redirector:
	
	This release does not support Novell's NetWare Client 32 redirector. For
	more information, please check the www.microsoft.com web site.
	
	Two Check Boxes Are Mutually Exclusive:
	
	On a server running File and Print Services for NetWare, two check boxes
	are mutually exclusive. These are the "Users Must Log On In Order To Change
	Password" check box (in the Account Policy dialog box) and the "User Must
	Change Password at Next Logon" check box (in the User Properties Dialog
	box).
	
	If the "Users Must Log On In Order To Change Password" check box is marked,
	then users who have the "User Must Change Password at Next Logon" check box
	marked in their accounts cannot use CHGPASS (or SETPASS or LOGIN) to change
	their passwords after they have logged on to the server.
	
	It is recommended that you do not select both these check boxes for File
	and Print Services for NetWare users.
	
	Using Windows NT Server as a Client to Connect to NetWare Servers:
	
	On a computer running Windows NT Server and File and Print Services for
	NetWare, the automatic restoration of connections from that computer to
	NetWare servers may not work if the computer does not have a preferred
	server selected, and a user logs in immediately after booting the computer.
	This happens because the Windows NT Server computer does not have time to
	gather information about available NetWare servers before attempting to
	restore connections.
	
	PRINTING NOTES
	
	Network Print Server Devices Tested:
	
	File and Print Services for NetWare has been tested with the following
	network print server devices:
	
	HP JetDirect cards
	
	Intel NetPort XL
	
	Xircom II series
	
	Milan FastPort 3000 series
	
	Digital NetPrint 100
	
	Emulex NetJet card
	
	AXIS NPS 550
	
	Extended Systems ESI2866A
	
	Castelle LANpress
	
	Setting Up the Milan Network Print Server Device:
	
	To successfully set up File and Print Services for NetWare to print to a
	printer attached to a Milan network print server device, use the following
	procedure:
	
	1. Use the Printers folder to create a logical printer for the printer. Be sure
	  to set the following in the Printer Properties dialog box:
	
	   - On the Ports tab, specify NetWareCompatiblePServer0 or
	     NetWareCompatiblePServer1 as the port.
	
	   - On the Sharing tab, mark the Shared check box.
	
	2. In Server Manager, click Print Servers from the FPNW menu.
	
	3. Click Add, and specify FPxxxxxx in the Print Server box, where xxxxxx are the
	  last 6 characters of the Milan MAC address. You can find the address printed
	  on the bottom of the device. Then click OK.
	
	4. Back in the Print Servers On dialog box, select the print server you created
	  in step 3, and then click Printers.
	
	5. In the Printers on Print Server dialog box, click Add.
	
	6. Fill out the Add Printer To dialog box with information for the printer. Be
	  sure to specify Remote Other/Unknown in the Type box. Then click OK.
	
	7. Back in the Printers on Print Server dialog box, click Queues, and add the
	  queue you created in step 1.
	
	Miscellaneous Printing Notes
	----------------------------
	
	If you find that print jobs sent from NetWare clients to File and Print
	Services for NetWare printers are not printing banner sheets, or are not
	notifying clients correctly, you should check certain printer properties.
	
	To check the printer properties:
	
	1. Open the Printers folder.
	
	2. Select the printer, and then choose Properties from the Printer menu.
	
	3. On the Ports tab, check that the port is set correctly, to either a
	  NetWareCompatiblePServer port or a local port, such as LPT1:
	
	4. On the Sharing tab, check that the printer has been shared on the network.
	
	5. On the General tab, click the Print Processor button, and then check that the
	  print processor is set to "nwprint."
	
	6. Click OK.
	
	7. Close the Printers folder, and then stop and restart the File and Print
	  Services for NetWare service.
	
	Similarly, if you have two printer queues that use the same printer, and
	one of the printer queues has the Job Type set to WINPRINT, then jobs in
	that queue may freeze with the message "Waiting for PServer", causing both
	queues to freeze. To correct this problem, stop and restart the print
	server software, or stop and restart the File and Print Services for
	NetWare service.
	
	Legal Notices
	-------------
	
	Third-Party License Agreements
	
	Administrators should ensure they comply with all applicable license
	agreements governing use of software in conjunction with File and Print
	Services for NetWare.
	
	Microsoft and Windows NT are registered trademarks of Microsoft
	Corporation in the U.S. and/or other countries.
	
	Novell and NetWare are registered trademarks and NetWare Client 32 is a
	trademark of Novell, Inc.
	
	Other companies and product names may be trademarks of their respective
	companies.
	======================================================================
	Keywords          : kbinterop 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbServicesNetwareSearch kbFPNW400
	Version           : WinNT:4.0
	Hardware          : ALPHA x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
