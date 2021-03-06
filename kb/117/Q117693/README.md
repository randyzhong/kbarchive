---
layout: page
title: "Q117693: PC Adm: Microsoft Mail MMFCLEAN.EXE Utility"
permalink: /kb/117/Q117693/
---

## Q117693: PC Adm: Microsoft Mail MMFCLEAN.EXE Utility

{% raw %}

	Article: Q117693
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.0,3.2
	Operating System(s): 
	Keyword(s): kbgraphxlinkcritical
	Last Modified: 21-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, versions 3.0, 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft provides MMFCLEAN.EXE, Windows-based application to be used on
	Microsoft Mail 3.0 and later postoffices to purge mail from mail message files
	(MMFs).
	
	For complete information about obtaining and installing MMFCLEAN.EXE, see the
	following sections:
	
	- To download the utility
	
	- To install MMFCLEAN.EXE
	
	MORE INFORMATION
	================
	
	Currently, there is no way for an administrator to monitor or manage space
	consumed by a Windows or OS/2 Mail user on a version 3.0 or later Microsoft Mail
	postoffice (PO). In versions of Microsoft Mail earlier than version 3.0, the
	administrator could purge mail messages for all users on the PO. When the mail
	message file (MMF) architecture of versions 3.0 and later of Microsoft Mail for
	Windows was introduced, the administrator lost the ability to purge mail
	messages stored in the MMFs.
	
	The MMFCLEAN utility is a Windows-based application to be used on Microsoft Mail
	3.0 and later postoffices to purge mail from MMFs. MMFs usually exist on the PO
	and contain the users' private mail messages and folders. There is one MMF per
	Windows user on the PO. By default, the Windows user will have his or her MMF
	file stored on the PO, but the user can choose to store the MMF file on his or
	her local machine. The MMFCLEAN utility matches the capability of the Mail
	Administrator program. The administrator should run it from a Windows 3.0 or
	3.1, or Windows for Workgroups 3.1 or 3.11 local area network (LAN) client
	connected to the PO over the network.
	
	You can use the MMFCLEAN utility to clean the MMF according to the following
	criteria:
	
	- Message Age days
	
	- All messages with size greater than XXX
	
	- Message priority
	
	Things to Note Before Running MMFCLEAN
	--------------------------------------
	
	WARNING: Before you use the MMFCLEAN utility to clean the database, make an
	additional backup copy of your Microsoft Mail postoffice. If an error occurs
	during a fix, you can restore the backup made immediately before you used the
	MMFCLEAN utility. In all other circumstances, you should restore the database
	from your most recent regularly scheduled backup.
	
	- Available disk space should be three times the size of the largest MMF.
	
	- Do not use an active PO; all users should be logged off and the PO should be
	  backed up.
	
	- File Scan is required for Novell networks.
	
	- MMFs not stored on the PO will not be included; any MMFs stored on a user's
	  local drive or on another server will not be cleaned.
	
	- No other Mail application should be running on the workstation when you start
	  the MMFCLEAN utility.
	
	- The Just Compress check box in the Criteria dialog box overrides all other
	  criteria. Remember that when a cleaning is done, a compress is also
	  automatically done.
	
	  Important: When MMFCLEAN does comparisons on the aging date, the creation date
	  of the message is used instead of the date the user received the message.
	  This means that if a user was on vacation for a week and then came in and
	  downloaded his new messages to his MMF, the user's message could get deleted
	  right after it is read if the criteria for MMFCLEAN is Read Mail Greater Than
	  7 Days. We are currently investigating how to change this limitation.
	
	To download the utility
	-----------------------
	
	The following file is available for download from the Microsoft Download Center:
	
	  DownloadDownload Mmfutil.exe now
	  (http://download.microsoft.com/download/pcmail/Utility/10/WIN/EN-US/Mmfutil.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	After you download MMFCLEAN.EXE to a clean directory, run it (by typing "mmfutil"
	(without the quotation marks) at the MS-DOS command prompt) to extract the
	contents of the file. You should receive the following files:
	
	  VMB.386      (  9,273 bytes, dated 02-24-92,  3:54 P.M.)
	  DEMILAYR.DLL ( 48,304 bytes, dated 07-01-93, 12:20 P.M.)
	  MAILMGR.DLL  ( 51,632 bytes, dated 07-01-93,  1:12 P.M.)
	  STORE.DLL    (231,264 bytes, dated 02-01-94,  2:40 P.M.)
	  MMFCLEAN.EXE ( 43,520 bytes, dated 10-12-94,  3:48 P.M.)
	  WX.EXE       ( 14,215 bytes, dated 03-03-92,  5:57 A.M.)
	  WXSRVR.EXE   ( 17,920 bytes, dated 03-03-92,  5:57 A.M.)
	  MMFCLEAN.INI (  1,398 bytes, dated 12-13-93, 10:54 A.M.)
	  README.TXT
	
	To install MMFCLEAN.EXE
	-----------------------
	
	1. At the MS-DOS command prompt, type the following and press ENTER
	
	  " mkdir <drive>:\mmfclean" (without the quotation marks)
	
	  where <drive> is the local hard disk drive.
	
	2. At the MS-DOS command prompt, type the following and press ENTER
	
	  " copy <srcdrive>:\*.dll <destdrive>:\mmfclean" (without the
	  quotation marks)
	
	  where <srcdrive> is the drive and directory where you ran the self-
	  extracting MMFUTIL.EXE file and <destdrive> is the drive and directory
	  where you created the MMFCLEAN directory. For example, if you ran the
	  self-extracting file from the TEST directory on drive D, and the MMFCLEAN
	  directory is located on drive C, type the following command:
	
	  " copy d:\test\*.dll c:\mmfclean" (without the quotation marks)
	
	3. At the MS-DOS command prompt, type the following and press ENTER
	
	  " copy <srcdrive>:\mmfclean.exe <destdrive>:\mmfclean" (without
	  the quotation marks)
	
	  where <srcdrive> is the drive and directory where you ran the self-
	  extracting MMFUTIL.EXE file and <destdrive> is the drive and directory
	  where you created the MMFCLEAN directory. For example, if you ran the
	  self-extracting file from the TEST directory on drive D, and the MMFCLEAN
	  directory is located on drive C, type the following command:
	
	  " copy d:\test\mmfclean.exe c:\mmfclean" (without the quotation marks)
	
	4. At the MS-DOS command prompt, type the following and press ENTER
	
	  " copy <srcdrive>:\mmfclean.ini <destdrive>:\<windowsdir>"
	  (without the quotation marks)
	
	  where <srcdrive> is the drive and directory where you ran the self-
	  extracting MMFUTIL.EXE file, <destdrive> is the drive where your
	  Windows directory is located, and <windowsdir> is the path to your
	  Windows directory. For example, if you ran the self-extracting file from the
	  TEST directory on drive D and the Windows directory is named WINDOWS and is
	  located on drive C, type the following command:
	
	  " copy d:\test\mmfclean.ini c:\windows" (without the quotation marks)
	
	5. Set up an MMFCLEAN icon in Windows Program Manager and set the working
	  directory to where MMFCLEAN.EXE is located.
	
	MMFCLEAN.INI Settings
	---------------------
	
	The MMFCLEAN.INI file must reside in the Windows directory.
	
	You can define the following parameters in the [Options] section of the
	MMFCLEAN.INI file. Some modifications to the .INI file are required before you
	run it for the first time.
	
	Parameter                           | Example/description
	--------------------------------------------------------------------
	Drive=<drive and path to            | Drive=m:\testpo
	postoffice>                         | -or-
	                                   | Drive=\\<server>\<share>\<path>
	                                   | -or-
	                                   | Drive=<server>/<share>:<path>
	                                   |
	Name=<administrator's mailbox name> | Name=Admin
	                                   |
	Password=<administrator's password> | Password=password
	                                   |
	MailAge=<default mail age days>     | MailAge=30
	                                   |
	MsgSize=<default message size       | MsgSize=20
	in kilobytes>                       |
	                                   |
	MsgPriority=<default message        | MsgPriority=3
	priority>                           |
	                                   | Here is how the numeric priorities
	                                   | relate to the Mail for Windows
	                                   | priorities: Priorities 1 & 2=Low,
	                                   | priority 3=Medium, and priorities
	                                   | 4 & 5=High.
	                                   |
	MMFSize=<minimum MMF size           | MMFSize=45
	in kilobytes>                       |
	                                   | MMFs smaller than the specified size
	                                   | are ignored. A value of zero means
	                                   | to accept all.
	                                   |
	OnlyReadMail=<delete only read      | OnlyReadMail=1
	mail 0/1>                           |
	                                   | 0 = Unread and Read
	                                   | 1 = Read mail only
	                                   |
	AllFolders=<0/1/2>                  | AllFolders=0
	                                   |
	                                   | Which folders should be searched:
	                                   |
	                                   | 0 = All folders
	                                   | 1 = Inbox, Sent mail, and Wastebasket
	                                   |     folders only
	                                   | 2 = Sent mail and Wastebasket
	                                   |     folders only
	                                   |
	LogFile=<path & name of log file>   | LogFile=c:\mmfclean\mmfclean.log
	                                   |
	JustLogUsers=<0/1>                  | JustLogUsers=0
	                                   |
	                                   | 1 = Only log user statistics to log
	                                   |     file-no cleaning or compression.
	                                   |
	JustCompress=<0/1>                  | JustCompress=0
	                                   |
	                                   | 1 = Only Compress MMFs-no cleaning.
	                                   |
	SkipBad=<0/1>                       | SkipBad=0
	                                   |
	                                   | Skip bad MMFs when processing-useful
	                                   | for overnight runs. Bad MMFs are
	                                   | logged for later interactive rebuild.
	                                   |
	                                   | SkipBad is ignored when WorkLocal=1.
	                                   |
	                                   | 0 = Do not skip bad MMFs, but bring
	                                   |     up a repair dialog box.
	                                   | 1 = Skip bad MMFs.
	                                   |
	WorkLocal=<0/1>                     | WorkLocal=0
	                                   |
	                                   | Copy MMFs to a local drive for
	                                   | processing. Useful if servers and
	                                   | networks are slow and you need
	                                   | increased performance.
	                                   |
	                                   | 0 = Don't copy, work off the server.
	                                   | 1 = Copy to local drive.
	                                   |
	LocalPath=<path>                    | LocalPath=c:\temp
	                                   | Destination path for MMFs that are
	                                   | being copied locally. Presence of
	                                   | this entry does not imply that
	                                   | WorkLocal=1. This is so you can have
	                                   | a path entry in your .INI file, but
	                                   | turn local processing on and off
	                                   | from the command line.
	
	MMFCLEAN Command-Line Options
	-----------------------------
	
	Usage: mmfclean [command-line options]
	
	Options                  | Description
	--------------------------------------------------------------------
	/P:<password>            | Admin password.
	                        |
	/N:<username>            | Admin user name.
	                        |
	/D:<drive>               | Postoffice path.
	                        |
	/A:<days>                | Mail age.
	                        |
	/G:<msgsize>             | All messages greater than.
	                        |
	/O:<1-5>                 | Mail priority less than or equal to.
	                        |
	/S:<mmfsize>             | Users with MMF size greater than.
	                        |
	/R                       | Only read mail.
	                        |
	/U                       | Both read and unread mail.
	                        |
	/F                       | Search all folders.
	                        |
	/I                       | Search Inbox, Sent Mail, Wastebasket only.
	                        |
	/W                       | Search Sent Mail and Wastebasket only.
	                        |
	/L:<logfilename>         | Log file.
	                        |
	/J                       | Log users-don't compress.
	                        |
	/C                       | Just compress-no cleaning.
	                        |
	/B                       | Batch mode-run immediately and exit after.
	                        |
	/K                       | Skip bad MMFs when processing.
	                        |
	/H                       | Copy files to local drive for processing; use
	                        | of this switch without /T or a corresponding
	                        | .INI file entry file causes MMFCLEAN to
	                        | default to the Windows directory.
	                        |
	/T:<path>                | Local path to which MMF files should be
	                        | copied for processing (/H switch); use of
	                        | this switch implies /H.
	
	Running MMFCLEAN in Batch Mode
	------------------------------
	
	To run the MMFCLEAN utility from an MS-DOS batch file, you need the VMB.386,
	WX.EXE, and WXSRVR.EXE utilities located with this utility. Copy VMB.386 to your
	Windows SYSTEM subdirectory, and copy WX.EXE and WXSRVR.EXE to your Windows
	directory. Additionally, you need to add the VMB.386 file to the [386Enh]
	section of your SYSTEM.INI file. For example:
	
	  [386Enh]
	  Device=vmb.386
	
	The VMB.386 file will allow you to run a Windows-based application from the
	MS-DOS prompt.
	
	WXSRVR.EXE is a Windows-based application that should be run from File Manager or
	Program Manager first. WX.EXE is an MS-DOS-based application that is run from
	the MS-DOS command prompt under Windows.
	
	Usage: wx [options] program [command-line options]
	
	Options                   | Description
	/A                        | Run program asynchronously.
	/H[ELP]                   | Call QuickHelp.
	/N[OLOGO]                 | Suppress copyright message.
	/W                        | Assume virtual machine (VM) is windowed.
	/?                        | Display summary help.
	
	Example: wx /w mmfclean.exe /a:20 /n:admin /p:password /u /b
	
	Troubleshooting
	---------------
	
	Log File Error Messages:
	
	1. Error:
	
	  Administrator Admin 00000000 42Kbytes
	  Cannot lock user's MMF file; could result in corruption.
	  Skipping user.
	
	  Cause: The user is logged into Mail or the file is open.
	
	2. Error:
	
	  Administrator Admin 00000000 42Kbytes
	  Error copying m:\mmf\00000000.mmf to C:\mmfTeMP\~~MMFKFC.TMP
	
	  Cause: The user no longer exists or was deleted.
	
	3. Error: USER1 USER1 00000005 577Kbytes Error opening C:\mmfTeMP\~~MMFJEA.TMP
	  Cause: The user's name or password in the MMF does not match the name or
	  password in the access files.
	
	4. Error:
	
	  Administrator Admin 00000000 42Kbytes
	  Error copying m:\mmf\00000000.mmf to C:\mmfTeMP\~~MMFNEC.TMP
	
	  Cause: There was not enough disk space on the local drive.
	
	Other Error Messages
	--------------------
	
	1. Error:
	
	  ! The version of STORE.DLL on your computer must be updated.
	
	  Cause: The working directory was not set to C:\MMFCLEAN.
	
	2. Error:
	
	  <STOP> An inconsistency has been detected in the mail message file.
	  This problem must be repaired before the mail file can continue to be used.
	  Repairs may take up to several hours depending on the number of messages you
	  have in your message file.
	
	  MMFClean Log information:
	
	  Username Username 00000005 39Kbytes
	  This MMF file is corrupt and was not automatically repaired.
	
	  Cause: A corrupt MMF was found. For more details, please refer to the
	  MMFCLEAN.LOG file.
	
	Additional query words: 3.20 wga
	
	======================================================================
	Keywords          : kbgraphxlinkcritical 
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN320 kbMailPCN300
	Version           : WINDOWS:3.0,3.2
	
	=============================================================================
	

{% endraw %}
