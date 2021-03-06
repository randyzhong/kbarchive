---
layout: page
title: "Q181942: XCLN: Cannot Resolve SMTP Addresses, Messages Sent Successfully"
permalink: /kb/181/Q181942/
---

## Q181942: XCLN: Cannot Resolve SMTP Addresses, Messages Sent Successfully

{% raw %}

	Article: Q181942
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:5.0; :8.01,8.02,8.03
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows NT client, version 5.0 
	- Microsoft Exchange Windows 95/98 client, version 5.0 
	- Microsoft Outlook 97, versions 8.01, 8.02, 8.03 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you address a message to a Simple Mail Transfer Protocol (SMTP) recipient
	that is located in your personal address book (PAB) or the global address list,
	the SMTP address may not be resolved. Your e-mail client may underline the SMTP
	address and send the message successfully, but the address is not resolved to
	the display name that appears in the PAB or global address list.
	
	CAUSE
	=====
	
	This problem can occur when one or more of the following files are damaged:
	
	- Emsabp32.dll
	
	- Emsui32.dll
	
	- Mapi32.dll
	
	- Wmsui.dll
	
	- Wmsui32.dll
	
	WORKAROUND
	==========
	
	To resolve this problem, verify that the above files are not damaged. To do so,
	use one of the following methods:
	
	- If you are using a Microsoft Exchange client, rename the files on your hard
	  disk, and then extract new copies of the files from the Microsoft Exchange
	  5.0 Client Pack CD-ROM. The following table lists the location of the files
	  on the CD-ROM:
	
	     File           Cabinet File
	     ---------------------------
	     Emsabp32.dll   Exchng4.cab
	     Emsui32.dll    Exchng4.cab
	     Mapi32.dll     Exchng5.cab
	     Wmsui.dll      Exchng7.cab
	     Wmsui32.dll    Exchng8.cab
	
	  NOTE: Windows 95 cabinet files are located in the Eng\Win95 folder on the
	  CD-ROM. Windows NT (Intel) cabinet files are located in the Eng\Winnt\I386
	  folder on the CD-ROM.
	
	- If you are using a Microsoft Outlook client, rename the files on your hard
	  disk, and then copy the files from the Outlook CD-ROM to your hard disk.
	
	- Reinstall your e-mail client.
	
	STATUS
	======
	
	Microsoft is researching this problem and will post additional information here
	in the Microsoft Knowledge Base as it becomes available.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbExchangeSearch kbExchangeClientSearch kbZNotKeyword kbZNotKeyword2 kbOutlook97Search kbZNotKeyword3 kbOutlook801 kbOutlook802 kbOutlook803 kbExchange500NT kbExchange500Win95
	Version           : WINDOWS:5.0; :8.01,8.02,8.03
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
