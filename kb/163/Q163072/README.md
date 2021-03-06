---
layout: page
title: "Q163072: Allow SNARAS to Use a Fully Qualified LU Name in Phone Number"
permalink: /kb/163/Q163072/
---

## Q163072: Allow SNARAS to Use a Fully Qualified LU Name in Phone Number

{% raw %}

	Article: Q163072
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When configuring SNA Server 2.11 to support an SNARAS connection on a computer
	running Windows NT Server 3.51, a Remote Access Service (RAS) phone book entry
	must be configured to specify the "phone number" of the remote system. The phone
	number must be specified in the following format:
	
	  <remote APPC LU alias> <mode name>
	
	However, SNARAS does not support the following format:
	
	  <fully qualified remote LU name> <mode name>
	
	For example, assume the following APPC LU/LU/mode partnership is defined in SNA
	Server:
	
	  Local APPC LU:
	     LU alias name = SNARASLU
	     Network name  = APPN
	     LU name = BRANCH1
	
	  Remote APPC LU:
	     LU alias name = BOSTON
	     Network name  = APPN
	     LU name       = BRANCH5
	
	  Mode name:  #INTER
	
	Then the RAS phone book entry for the SNARAS connection would be configured as
	the following:
	
	  phone number: BOSTON #INTER
	
	The following phone book entry is also now supported:
	
	  phone number: APPN.BRANCH5 #INTER
	
	NOTE: The fully qualified LU name is identified by the period (.) that separates
	the remote network name and the remote APPN LU name. This forms the fully
	qualified remote APPC LU name.
	
	CAUSE
	=====
	
	SNA Server 2.11 and 2.11 Service Pack 1 SNARAS does not support the phone number
	entry to specify a fully qualified Remote APPC LU name.
	
	RESOLUTION
	==========
	
	An SNA Server 2.11 update to SNARAS that supports the ability to specify the
	fully qualified Remote APPC LU name in the phone number entry is now available.
	
	The updated SNA Server 2.11 modules are Snaras.dll and Rassna.dll.
	
	SNA Server 3.0 already supports either format (the LU alias or the fully
	qualified LU name). Also, because SNA Server 3.0 supports the dynamic creation
	of remote APPC LUs (by enabling the "Supports Dynamic Remote APPC LU Definition"
	option on the connection), it is not necessary to manually create a remote APPC
	LU for each remote SNARAS destination, as it is under SNA Server 2.11. When
	configuring the SNARAS phone book entry to use a fully qualified remote APPC LU
	name, SNA Server 3.0 dynamically creates this remote APPC LU when SNARAS
	attempts to start the connection.
	
	NOTE: The Windows NT Server 3.51 Remote Access Service (RAS) doesn't allow the
	user to override the configured SNARAS phone number using the RASDIAL command.
	For example, the following command does not work:
	
	  rasdial BOSTON /phone:"NEWYORK #INTER"
	
	Using Windows NT Server 4.0, it is now possible to override the phone number for
	the SNARAS connection.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server version
	2.11 and 2.11 Service Pack 1.
	
	
	A supported fix is now available, but is not fully regression-tested and should
	be applied only to systems experiencing this specific problem. Unless you are
	severely impacted by this specific problem, Microsoft recommends that you wait
	for the next Service Pack that contains this fix. Contact Microsoft Technical
	Support for more information.
	
	
	
	Additional query words: sp1 prodsna
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ211 kbSNAServ211SP1
	Version           : WINDOWS:2.11,2.11 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
