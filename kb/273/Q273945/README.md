---
layout: page
title: "Q273945: XCON: X.400 Connector Ignores OU2 During Routing"
permalink: /kb/273/Q273945/
---

## Q273945: XCON: X.400 Connector Ignores OU2 During Routing

{% raw %}

	Article: Q273945
	Product(s): Microsoft Exchange
	Version(s): 5.5,5.5 SP1,5.5 SP2,5.5 SP3
	Operating System(s): 
	Keyword(s): exc55 exc55sp1 exc55sp2 exc55sp3 kbExchange550preSP5fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2, 5.5 SP3 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Exchange Server message transfer agent (MTA) may choose a wrong route when
	connections have an address space that is defined using an Organizational Unit 2
	(OU2). Messages may bounce, and non-delivery reports (NDRs) may be created.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Exchange Server version 5.5 service pack that contains
	this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The fix needs to be installed in all routing calculation servers in the
	organization.
	
	For customers that are routing on OUs and that do not upgrade all their routing
	ID servers together, the following problems will occur:
	
	- This present problem will appear on the messages that get routed by the MTAs
	  that do not have the fix applied.
	
	- When one of the servers with the fixed Gateway Address Resolution Table
	  (GWART) replicates the GWART over to other servers, the other server without
	  the fix generates a different GWART, and replicates its version of the GWART,
	  creating a "ping-pong" effect in replication. The servers with the fix and
	  the server without will generate a different GWART for the same data and
	  connectors, and duel over whose copy of the GWART is correct. The bare
	  minimum requirement is that all the routing ID servers be updated together.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: MTA
	
	+----------------------------+
	| File name    | Version     | 
	+----------------------------+
	| Emsmta.exe   | 5.5.2654.21 | 
	+----------------------------+
	| Ems_rid.dll  | 5.5.2654.21 | 
	+----------------------------+
	| MTacheck.exe | 5.5.2654.21 | 
	+----------------------------+
	| Mtamsg.dll   | 5.5.2654.21 | 
	+----------------------------+
	| X400om.dll   | 5.5.2654.21 | 
	+----------------------------+
	| Mtaperf.dll  | 5.5.2654.21 | 
	+----------------------------+
	| P2.xv2       | n/a         | 
	+----------------------------+
	| P772.tpl     | n/a         | 
	+----------------------------+
	| P42.tpl      | n/a         | 
	+----------------------------+
	| Dbserver.sch | n/a         | 
	+----------------------------+
	| Dcprods.cat  | n/a         | 
	+----------------------------+
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 exc55sp1 exc55sp2 exc55sp3 kbExchange550preSP5fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2 kbExchange550SP3
	Version           : :5.5,5.5 SP1,5.5 SP2,5.5 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
