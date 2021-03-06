---
layout: page
title: "Q235837: SMS: LAN_SENDER Doesn't Fail Job When No Instruction File Exists"
permalink: /kb/235/Q235837/
---

## Q235837: SMS: LAN_SENDER Doesn't Fail Job When No Instruction File Exists

{% raw %}

	Article: Q235837
	Product(s): Microsoft Systems Management Server
	Version(s): 1.2 SP4
	Operating System(s): 
	Keyword(s): kbServer kbsms120 kbsms120bug kbPackage kbScheduler kbSoftwareDist
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the SMS_LAN_SENDER component receives a send request from the Scheduler, it
	does not determine whether there is a valid instruction file in the
	\Schedule.box\Tosend directory before trying to send the package file. After
	sending the package file, SMS_LAN_SENDER tries sending the instruction file. If
	the file does not exist, it simply reschedules the send request to try again
	later.
	
	This can result in a situation where the package file keeps being re-sent to the
	destination site without a corresponding instruction file, and a zero byte file
	is created on the destination site. If the package were a large one, this could
	quickly consume the drive space on a remote site.
	
	
	WORKAROUND
	==========
	
	To work around this behavior, you can manually delete the zero byte files from
	the Despoolr.box\Receive directory on the central site.
	
	STATUS
	======
	
	A supported fix that corrects this problem is now available from Microsoft, but
	it has not been fully regression tested and should be applied only to computers
	that are experiencing this specific problem. If you are not severely affected by
	this specific problem, Microsoft recommends that you wait for the next Systems
	Management Server service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	+------------------------------------------------------+
	| Date     | Time    | Size    | File name  | Platform | 
	+------------------------------------------------------+
	| 21/12/00 | 10:36AM | 133,536 | sender.dll | i386     | 
	+------------------------------------------------------+
	| 21/12/00 | 10:37AM | 211,216 | sender.dll | Alpha    | 
	+------------------------------------------------------+
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	Additional query words: prodsms lansend
	
	======================================================================
	Keywords          : kbServer kbsms120 kbsms120bug kbPackage kbScheduler kbSoftwareDist 
	Technology        : kbSMSSearch kbSMS120SP4
	Version           : :1.2 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
