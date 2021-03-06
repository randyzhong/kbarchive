---
layout: page
title: "Q112304: PC Win: MOVEUSER.EXE Err Msg: Export User Failed"
permalink: /kb/112/Q112304/
---

## Q112304: PC Win: MOVEUSER.EXE Err Msg: Export User Failed

{% raw %}

	Article: Q112304
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.0,3.0b,3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for Windows, versions 3.0, 3.0b, 3.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the MOVEUSER.EXE program to export a user to an .MMU file (using
	the Export option under the File menu), the following error may occur:
	
	  Export user Failed
	
	When you use the MOVEUSER.EXE program to copy a user from one postoffice to
	another postoffice, the following error message may occur
	
	  Moving user <User Name> Failed
	
	where <User Name> is the full name of the user being moved.
	
	CAUSE
	=====
	
	This problem can occur if the .MAI files corresponding to the messages in the
	user's .MBG file are missing.
	
	The MOVEUSER.EXE program tries to read and save all the user's mail. It does this
	by reading the user's .KEY file to determine which message headers present in
	the user's .MBG file are not deleted. Each header in the .MBG file contains the
	name of the .MAI file containing the message. While going through the .MBG file,
	if MOVEUSER.EXE detects that the .MAI file for a header is missing, the above
	error messages are generated.
	
	The problem of a missing .MAI file also manifests itself with the following error
	message when the corresponding mail message is read from the MS-DOS
	workstation:
	
	  Notice 16
	  Error reading mail
	  (Possibly previously deleted)
	
	RESOLUTION
	==========
	
	This problem can be resolved in one of the following three ways:
	
	- Delete the message(s) from the Microsoft Mail MS-DOS client.
	
	- Restore the missing .MAI file(s) from a backup copy.
	
	- Clear all the pointers to any lost MAIs.
	
	To determine the .MAI file for the message in question
	------------------------------------------------------
	
	1. Use the USRDMP.EXE or LISTUSER.EXE utility to get the user's 8-digit ID.
	  These utilities are available to Mail administrators as part of the "Database
	  Maintenance Utilities" document.
	
	  To obtain these utilities, please see the following article in the Microsoft
	  Knowledge Base:
	
	  Q99419 PC DB: Database Maintenance Utilities (Complete)
	
	2. The user's .MBG file is <8-digit ID>.MBG and is present in the MBG
	  subdirectory of the Microsoft Mail postoffice.
	
	3. From the user's .MBG file, you can determine the corresponding .MAI file for
	  the message in question.
	
	To clear all the pointers to any lost MAIs:
	-------------------------------------------
	
	1. Login to the user's account with the Windows client and spool all his or her
	  mail into his or her .MMF.
	
	2. Reset the <hexid>.KEY and <hexid>.MBG.
	
	This will clear all the pointers to any lost MAIs and will allow you to move the
	user to the new postoffice.
	
	MORE INFORMATION
	================
	
	
	Additional query words: 3.00 3.00b 3.20 DBUTILS PSS
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMail300 kbMail320 kbMail300b
	Version           : WINDOWS:3.0,3.0b,3.2
	
	=============================================================================
	

{% endraw %}
