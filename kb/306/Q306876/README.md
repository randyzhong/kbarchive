---
layout: page
title: "Q306876: APPC/CPI-C App. Doesn't Use APPC LU With Auto-activated Sessions"
permalink: /kb/306/Q306876/
---

## Q306876: APPC/CPI-C App. Doesn't Use APPC LU With Auto-activated Sessions

{% raw %}

	Article: Q306876
	Product(s): Microsoft SNA Server
	Version(s): 
	Operating System(s): 
	Keyword(s): kbDSupport kbhis2000 kbhis2000bug
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An Advanced Program-to-Program Communication (APPC) or Common Programming
	Interface for Communications (CPI-C) application may fail to allocate a
	conversation even though there are auto-activated (or pre-allocated) LU 6.2
	sessions available for the remote APPC LU and APPC mode specified by the
	application.
	
	The specific errors returned by the application may vary when this occurs. The
	following are typical APPC and CPI-C errors returned to the application.
	
	If this occurs with an APPC application, the [MC_]ALLOCATE fails with the
	following error message:
	
	  primary_rc = 0x0003 (AP_ALLOCATION_ERROR)
	  secondary_rc = 0x00000005 (AP_ALLOCATION_FAILURE_RETRY)
	
	A CPIC application fails with the following error message:
	
	  rc = 20 (CM_PRODUCT_SPECIFIC_ERROR)
	
	In addition, the following event may also be logged in the Application Event
	log:
	
	  Event ID: 93
	  Source: SNA APPC Application
	  Description: APPC local conversation start failed:
	
	  Primary_rc = 0003
	  Secondary_rc = 00000005
	  TP_ID = <value>
	  Dest TP name = <value>
	  LU alias = <value>
	  PLU alias = <value>
	  Mode name = <value>
	  FQ PLU name = <value>
	
	NOTE: These particular errors are fairly common APPC and CPI-C errors, so they
	may occur for reasons other then the one described here.
	
	APPC or CPI-C applications that had been functioning correctly when the
	application was obtaining LU 6.2 sessions through a Microsoft SNA Server 3.0 or
	4.0 system may start experiencing this problem when the SNA Server systems are
	upgraded to Host Integration Server 2000 because this particular problem does
	not exist in previous versions of SNA Server.
	
	CAUSE
	=====
	
	The SNA Server service (Snaservr.exe) in Host Integration Server 2000 does not
	properly initialize a variable under some circumstances. This prevents the SNA
	Server service from selecting the "best" local APPC LU for an LU 6.2 (APPC)
	session request.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Host Integration Server 2000 service pack that contains
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
	
	The English version of this fix should have the following file attributes or
	later:
	
	+-------------------------------------+
	| File name    | Date       | Time    | 
	+-------------------------------------+
	| Snaservr.exe | 08/31/2001 | 03:51PM | 
	+-------------------------------------+
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Host Integration
	Server 2000.
	
	MORE INFORMATION
	================
	
	The problem described here occurs under the following circumstances:
	
	- The APPC mode that is used by the APPC or CPI-C application is configured to
	  auto-activate LU 6.2 sessions.
	
	- Explicit APPC partnerships are configured in the APPC mode that the
	  application is using.
	
	- The local APPC LUs defined in SNA Manager have the Member of Default Outgoing
	  Local APPC LU Pool option enabled.
	
	- The APPC or CPI-C application does not specify a default local APPC LU alias
	  in its LU 6.2 session request.
	
	The following is an example of such a SNA configuration:
	
	Local APPC LUs:
	
	+-----------------------------------+
	| LU alias | Network name | LU name | 
	+-----------------------------------+
	| LOCAL1   | APPN         | LOCAL1  | 
	+-----------------------------------+
	| LOCAL2   | APPN         | LOCAL2  | 
	+-----------------------------------+
	
	Both of the local APPC LUs are configured to be members of the default outgoing
	local APPC LU pool.
	
	Remote APPC LUs:
	
	+-----------------------------------+
	| LU alias | Network name | LU name | 
	+-----------------------------------+
	| REMOTE1  | APPN         | REMOTE1 | 
	+-----------------------------------+
	| REMOTE2  | APPN         | REMOTE2 | 
	+-----------------------------------+
	
	The session limits for APPC Mode APPCMODE are defined as follows:
	
	+------------------------------------------+
	| Parallel session limit               | 8 | 
	+------------------------------------------+
	| Min. contention winner limit         | 4 | 
	+------------------------------------------+
	| Partner min. contention winner limit | 0 | 
	+------------------------------------------+
	| Automatic activation limit           | 4 | 
	+------------------------------------------+
	
	The following explicit APPC partnerships are defined for APPCMODE:
	
	+----------------------------------------------+
	| Server  | Local LU | Partner LU | Connection | 
	+----------------------------------------------+
	| SERVER1 | LOCAL1   | REMOTE1    | HOST       | 
	+----------------------------------------------+
	| SERVER1 | LOCAL2   | REMOTE2    | HOST       | 
	+----------------------------------------------+
	
	When you are using this configuration, SNA Server 3.0 or 4.0 and Host Integration
	Server 2000 will auto-activate four sessions over each of the two explicit APPC
	partnerships that are defined for APPCMODE when the connection (HOST) is
	activated.
	
	When SNA Server 3.0 or 4.0 receives a session request from an APPC or CPI-C
	application that specifies a remote APPC LU of REMOTE1 and mode APPCMODE, the
	SNA Server will return LOCAL1 as the local LU alias to use for the LU 6.2
	conversation. This occurs because there are four contention winner sessions
	auto-activated for the APPC triplet LOCAL1/REMOTE1/APPCMODE that is currently
	available.
	
	Under the same conditions, Host Integration Server 2000 may return LOCAL2 to the
	application as the local LU alias to use instead of LOCAL1. If LOCAL2 is not a
	valid APPC LU for the host application being used, the APPC [MC_]ALLOCATE will
	fail as described previously. Even if LOCAL2 is valid, it may not be desirable
	to use LOCAL2 with REMOTE1.
	
	Any of the local APPC LUs that are members of the default outgoing local APPC LU
	pool are valid to use with any remote APPC LU and APPC mode because of the way
	that SNA Server 3.0/4.0 and Host Integration Server 2000 dynamically partner
	APPC LUs. However, a local APPC LU that has an available contention winner
	session with the requested remote APPC LU and mode should be the preferred local
	APPC LU. Auto-activated sessions are contention winner sessions.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDSupport kbhis2000 kbhis2000bug 
	Technology        : kbAudDeveloper kbHostIntegServ2000
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
