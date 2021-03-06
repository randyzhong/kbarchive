---
layout: page
title: "Q149852: XCLN: Newprof Can Tell New Profiles to Deliver Mail to PST"
permalink: /kb/149/Q149852/
---

## Q149852: XCLN: Newprof Can Tell New Profiles to Deliver Mail to PST

{% raw %}

	Article: Q149852
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 25-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 3.x client, versions 4.0, 5.0 
	- Microsoft Exchange Windows NT client, versions 4.0, 5.0 
	- Microsoft Exchange Windows 95/98 client, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Exchange Automatic Profile Generator (Newprof.exe) reads a Profile
	Descriptor File (.Prf) and creates a profile based on the information in this
	file.
	
	This article describes the changes that need to be made to the Default.prf file,
	present in the client installation directory, in order to create a profile with
	the default delivery location set to a local PST file. If the Default.prf is not
	present in the client installation directory, run the Microsoft Exchange Setup
	Editor.
	
	After the Default.prf file is modified with the changes outlined in this article,
	when users run the Microsoft Exchange Client Setup program, a profile will be
	automatically created for them and this profile will have a PST file which will
	be set as the default delivery store.
	
	MORE INFORMATION
	================
	
	In order to set a local PST file as the default delivery location for a profile,
	follow the steps below:
	
	1. Edit the Default.prf file on the client installation share point.
	
	2. Search for the [Service List] section which lists all the services to be
	  added to the profile.
	
	3. Look for an entry with the value Personal Folders. If it is present, note the
	  entry name. For example if the entry was:
	
	     Service2 = Personal Folders
	
	  The entry name is Service2.
	
	4. If an entry with the value of Personal Folders is not present, add a new
	  entry to the [Service List] section with Service2. If Service2 was already
	  taken with another service, make sure to change that service to the next
	  available service entry. So, if the Microsoft Exchange Server was Service2,
	  modify Microsoft Exchange Server to the next available Service entry. For
	  Example, if the last entry in the section has the name Service3, then the
	  next available entry will be Service4. Add the following lines to the
	  section:
	
	    Service2 = Personal Folders
	    Service4 = Microsoft Exchange Server
	
	5. In the Default.prf file, search for the [General] section. Make sure the
	  following line is present in the [General] section:
	
	     DefaultStore= Service2
	
	6. Add the following section:
	
	  [Service2]
	  PathToPersonalFolders= c:\exchange\mailbox.pst
	  RememberPassword=TRUE
	  EncryptionType=0x40000000
	  Password=
	
	After making the changes outlined above, the Default.prf in the client
	installation share point should have the following sections:
	
	  ; ***********************************
	  ; Section 1 - Profile defaults.
	
	  [General]
	  ProfileName=Delivery to  Local PST
	  DefaultProfile=Yes
	  OverwriteProfile=Yes
	  DefaultStore=Service2
	
	  ; *************************************
	  ; *************************************
	  ; *************************************
	  ; Section 2 - Services and clients in profile.
	
	  [Service List]
	  Service1=Microsoft Exchange Client
	  Service2=Personal Folders
	  Service3=Personal Address Book
	  Service4=Microsoft Exchange Server
	
	  ; *************************************
	  ; *************************************
	  ; *************************************
	  ; Section 3 - Default values for each service and client.
	
	  [Service2]
	  PathToPersonalFolders=c:\exchange\mailbox.pst
	  RememberPassword=TRUE
	  EncryptionType=0x40000000
	  Password=
	  ; *************************************
	
	After the above changes have been made to the Default.prf file in the client
	installation directory, users will have to run the Microsoft Exchange Client
	Setup program for the profile to be automatically generated. This profile should
	have the file Exchange\Mailbox.pst set as the default delivery store.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbExchangeClientSearch kbZNotKeyword kbZNotKeyword2 kbZNotKeyword3 kbExchange400NT kbExchange500NT kbExchange400Win95 kbExchange500Win95
	Version           : WINDOWS:4.0,5.0
	
	=============================================================================
	

{% endraw %}
