---
layout: page
title: "Q290621: XADM: Public Folder Rules Are Disabled w. Antivirus API Solution"
permalink: /kb/290/Q290621/
---

## Q290621: XADM: Public Folder Rules Are Disabled w. Antivirus API Solution

{% raw %}

	Article: Q290621
	Product(s): Microsoft Exchange
	Version(s): 5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Operating System(s): 
	Keyword(s): kberrmsg kbExchange550preSP5fix
	Last Modified: 18-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2, 5.5 SP3, 5.5 SP4 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	
	SYMPTOMS
	========
	
	When an Exchange Server administrator or public folder owner examines the rules
	that are defined on a public folder, the rules may be marked with a red "X,"
	which indicates that the rule is in error. The following events may be logged in
	the Application event log:
	
	  Source: MSExchangeIS Public
	  Type: Error
	  Category Rules
	  EventID: 1041
	  Description:
	  The rule (1-CF0) with sequence number 100 is being disabled due to errors
	  encountered while applying the rule. The public folder is PublicFolderName.
	
	  Source MSExchangeIS Public
	  Type: Error
	  Category: Transport Delivering
	  EventID: 2028
	  Description:
	  The delivery of a message sent by a public folder
	  /o=MICROSOFT/ou=SITENAME/cn=RECIPIENTS/cn=PublicFolderName213E31CA213E31CA213E31CA18482398000BC1
	  has failed
	  To: Recipient
	  Cc:
	
	CAUSE
	=====
	
	This problem can occur if an antivirus solution that is based on the antivirus
	application programming interface (API) is under stress on the Exchange Server
	5.5 computer at the same time that an autoforward-type public folder rule is
	running. When a post is made to the public folder, the rule generates a new
	message to deliver to the recipients that are specified in the rule. Because the
	post contains an attachment, the attachment must be submitted to the antivirus
	vendor for scanning. If the new message is being scanned when the message
	delivery is attempted, the Exchange Server computer attempts to deliver the
	message several times, with a delay between each attempt. This behavior can be
	controlled by modifying two registry keys that are described in the "Workaround"
	section of this article.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Microsoft Exchange Server 5.5 service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Information store
	
	+-------------------------+
	| File name | Version     | 
	+-------------------------+
	| Store.exe | 5.5.2654.93 | 
	+-------------------------+
	
	NOTE: Because of file dependencies, this fix requires Microsoft Exchange Server
	version 5.5 Service Pack 4.
	
	
	
	WORKAROUND
	==========
	
	To work around this problem if you are an Exchange Server administrator, examine
	and adjust the SendRetries and SendRetryInterval registry values for your
	environment. However, if this problem still occurs after you make adjustments to
	these registry values, you might need to apply the fix that is described in the
	"Resolution" section of this article.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To adjust the SendRetries and SendRetryInterval values:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the SendRetries value under the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSExchangeIS\VirusScan
	
	3. On the Edit menu, click REG_DWORD, change this decimal value as applicable
	  (the default value is 2), and then click OK.
	
	  When a client sends a message that contains an attachment, the attachment must
	  be scanned before the message is sent. If the message delivery process
	  determines that the attachment is currently being scanned, the information
	  store attempts to resend the message. This value specifies the number of
	  times that the information store attempts to resend the message, including
	  the first attempt to deliver the message. If you increase this value, you
	  provide more opportunities for messages to be processed. If you modify this
	  value, along with the SendRetryInterval value, delivery times might be
	  extended.
	
	4. Locate the SendRetryInterval value under the following key in the registry:
	
	  HKEY_LOCAL_HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\MSExchangeIS\VirusScan
	
	5. On the Edit menu, click REG_DWORD, change this decimal value as applicable
	  (the default value is 60000), and then click OK.
	
	  When a message is being sent, if that message contains an attachment that is
	  currently being scanned, the information store waits for a certain time
	  interval, and then the information store attempts to redeliver the message.
	  This value specifies the interval in milliseconds that the information store
	  waits before the information store attempts to redeliver the message. If this
	  value is set too high, delays might occur when messages are sent. If this
	  value is set too low, messages might expire from the sending queue because
	  the number of send retries might be exceeded before the scanning process for
	  the message is complete.
	
	6. Quit Registry Editor.
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Exchange Server
	version 5.5.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbExchange550preSP5fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2 kbExchange550SP3 kbExchange550SP4
	Version           : :5.5,5.5 SP1,5.5 SP2,5.5 SP3,5.5 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
