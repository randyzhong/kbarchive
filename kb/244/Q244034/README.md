---
layout: page
title: "Q244034: SMS: Window 95/98 Clients Hang Opening E-mail Attachments"
permalink: /kb/244/Q244034/
---

## Q244034: SMS: Window 95/98 Clients Hang Opening E-mail Attachments

{% raw %}

	Article: Q244034
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbsms200bug kbsms200fix kbsms200sp2fix
	Last Modified: 25-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Microsoft Windows 95-based or Microsoft Windows 98-based computer that is
	running the Systems Management Server 2.0 client may stop responding (hang) when
	you open an e-mail attachment or associated file.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0. This problem was first corrected in Systems Management Server
	version 2.0 Service Pack 2.
	
	MORE INFORMATION
	================
	
	To install the hotfix:
	
	1. Log on to your site server using an account with administrative privileges.
	
	2. On the site server, close the SMS Administrator console.
	
	3. Run the Q244034.exe hotfix file you received and follow the directions in the
	  wizard.
	
	After the wizard is finished, allow the updated Compver.ini and Clicore.exe files
	to be propagated to all Logon Points and/or Client Access Points (CAPS) in the
	site.
	
	NOTE: The default Client Configuration Installation Manager (CCIM) polling
	interval is 23 hours. Therefore, it may take up to 23 hours for the hotfix files
	to be propagated to the clients. To speed up this process, use any of the
	following methods:
	
	- Stop and restart the SMS Client Service on each client. For Microsoft Windows
	  NT, simply stop and restart the service. For Windows 95 or Windows 98, a
	  restart is required.
	
	- Create a software distribution for one of the Resource Kit tools (Setevnt.exe
	  or Cliutils.exe), along with the appropriate parameters to start a CCIM work
	  cycle. The tools are located on Systems Management Server (SMS) 2.0 CD-ROM
	  2.
	
	  For Setevnt.exe the syntax is:
	
	  setevnt /q
	
	  For Cliutils.exe, the syntax is:
	
	  Cliutils KICK "Client Configuration Installation Manager"
	
	- If you have the Networking Logon Client Installation option enabled, have
	  users log off and back on.
	
	- Have users run SMSMan manually.
	
	NOTE: Windows 95/98 clients may require a restart after the hotfix files have
	been installed to receive full hotfix functionality. To verify this, review the
	Clicore.log file after the update. If a restart is required, the entry listed
	below is logged. Because of the nature of this hotfix, Microsoft recommends that
	a mandatory restart policy be used for all Windows 95/98 computers after the
	hotfix has been applied.
	
	  Reboot required - disabling component until reboot
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsms200bug kbsms200fix kbsms200sp2fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
