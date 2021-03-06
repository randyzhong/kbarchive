---
layout: page
title: "Q109256: CONN: Changing Mail Connection Proxy Network &amp; Postoffice"
permalink: /kb/109/Q109256/
---

## Q109256: CONN: Changing Mail Connection Proxy Network &amp; Postoffice

{% raw %}

	Article: Q109256
	Product(s): Microsoft Mail For PC Networks
	Version(s): 3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Connection for PC and AppleTalk Networks, version 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	During installation of version 3.2 of the Microsoft Mail Connection for PC and
	AppleTalk Networks, the Mail for PC Networks administrator is asked to define
	the proxy network and postoffice names that will be used to represent the Mail
	for AppleTalk Networks system. If the administrator accepts the default values
	during installation, the proxy network and postoffice names will be
	MACNET/MACPO.
	
	Below are instructions for changing the proxy network and postoffice names from
	the default values.
	
	NOTE: DO NOT change the proxy network and postoffice names by editing the
	MACGATE.INI file.
	
	
	To change the proxy network/postoffice name on the gateway postoffice
	---------------------------------------------------------------------
	
	WARNING: Changing your proxy network or postoffice name invalidates all Mail for
	AppleTalk Networks addresses that have been added to global groups, Mail for PC
	Networks users' Personal Address Books (PABs), personal groups, and Remote
	client address lists.
	
	1. Remove all Mail for AppleTalk Networks addresses from Mail for PC Networks by
	  choosing Remove Mac Names From PC from the Connection Name Utility's
	  (CNU[ASCII 146]s) File menu. The Mail for AppleTalk Networks addresses are
	  automatically removed from all Mail for PC Networks postoffices that
	  participate in Directory Synchronization (Dir-Sync) after the next Dir-Sync
	  cycle. Do not continue until the Mail for AppleTalk Networks addresses have
	  been removed from Mail for PC Networks.
	
	2. Disable the Mail for PC Networks side of the gateway (terminate the
	  MACGATE.EXE program).
	
	3. Run the Mail Connection 3.2 PC Setup program and select Modify MS Mail
	  Connection On A Gateway/Downstream Postoffice. Enter the path to your
	  MAILDATA and MAILEXE directories and change the proxy network and postoffice
	  names.
	
	  NOTE: You must enter a unique network name for the proxy network.
	
	4. Remove the old proxy network/postoffice requestor record from the Dir- Sync
	  server postoffice and add the new proxy network and postoffice as a Dir-Sync
	  requestor:
	
	  a. Run the Mail for PC Networks Administrator utility on the Dir-Sync server
	     postoffice.
	
	  b. Select Config, Dir-Sync, Server, Requestor, Delete to delete the old
	     requestor record.
	
	  c. Select Config Dir-Sync, Server, Requestor, Create to define the new proxy
	     network and postoffice as a Dir-Sync requestor.
	
	  NOTE: Make sure you enter the same password that was used for the old proxy
	  network/postoffice requestor record.
	
	5. Log in to the Mail for AppleTalk Networks gateway server as the Network
	  Manager. From the Mail menu, choose Gateway, then Configuration. Confirm that
	  the new proxy network and postoffice names appear on the Mail connection
	  gateway configuration screen and click the Update button to continue.
	
	  NOTE: You MUST click the Update button to update the internal Mail for
	  AppleTalk Networks gateway configuration record after changing your proxy
	  network or postoffice name.
	
	  Export the complete Mail for AppleTalk Networks directory to the Mail for PC
	  Networks Dir-Sync server postoffice by means of the CNU. From the CNU File
	  menu, choose Export Directory, then click the Complete Directory button.
	
	6. Start the PC side of the gateway by executing the MACGATE.EXE program.
	
	7. The Mail for AppleTalk Networks addresses should reappear in the Global
	  Address List (GAL) and under the new proxy network/postoffice list after the
	  next Dir-Sync cycle is completed.
	
	  NOTE: The Dir-Sync server postoffice reports this error message during the
	  first Dir-Sync cycle after the proxy network or postoffice name change. You
	  can disregard it.
	
	  Error [138] Server sync does not exist anymore (22)
	
	To change the proxy network/postoffice name on downstream postoffices
	---------------------------------------------------------------------
	
	1. Disable any Mail for PC Networks Externals or gateways that process mail on
	  the downstream postoffice.
	
	2. Run the Mail Connection 3.2 PC Setup program and Select Modify MS Mail
	  Connection On A Gateway/Downstream Postoffice. The Setup program prompts you
	  to enter the path to your MAILDATA directory, your current (old) proxy
	  network and postoffice names, and the network and postoffice name of the
	  gateway postoffice. Then enter your new proxy network and/or postoffice
	  names.
	
	  NOTE: The proxy network and postoffice names on the downstream postoffice must
	  match the proxy network and postoffice names on the gateway postoffice.
	
	3. Restart any Mail for PC Networks Externals or gateways you disabled in step
	  1.
	
	4. Request a complete directory import with Dir-Sync by running the Mail for PC
	  Networks Administrator program (ADMIN.EXE) and selecting Config, Dir-Sync,
	  Requestor, Import.
	
	5. The Mail for AppleTalk Networks addresses should reappear in the GAL and
	  under the new proxy network/postoffice list after the next Dir-Sync cycle is
	  completed.
	
	To update Remote client address lists
	-------------------------------------
	
	WARNING: Changing the proxy network or postoffice name invalidates all Mail for
	AppleTalk Networks addresses for Remote client users.
	
	Regenerate the default directory view for Remote client users by running the Mail
	for PC Networks Administrator program and selecting Remote, Regenerate.
	
	The Remote client users should download the new directory during their next
	on-line session.
	
	
	Note that this article is referred to by the GTWAY article "How to Reset the Mail
	Queue for Mail Connection 3.2" Q134378. If you modify or delete this article,
	please make corresponding changes in that article.
	
	Note that this article is referred to by the GTWAY article "CONN: Setup Error
	Indicates Duplicate Gateway" Q141583. If you modify or delete this article,
	please make corresponding changes in that article.
	
	Additional query words: 3.20 FFAPI DirSync Dirsynch Admin
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailConn320
	Version           : :3.2
	
	=============================================================================
	

{% endraw %}
