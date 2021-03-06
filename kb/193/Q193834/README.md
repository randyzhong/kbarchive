---
layout: page
title: "Q193834: Behavior of Unreachable Demand Dial Interfaces in RRAS"
permalink: /kb/193/Q193834/
---

## Q193834: Behavior of Unreachable Demand Dial Interfaces in RRAS

{% raw %}

	Article: Q193834
	Product(s): Microsoft Windows NT
	Version(s): 2000,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Routing and Remote Access Service Update for Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows 2000 Advanced Server 
	- Microsoft Windows 2000 Server 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SUMMARY
	=======
	
	This article is intended to describe the characteristics of the Routing and
	Remote Access Service (RRAS) when a Dial on Demand (DOD) interface attempts to
	dial a number that is not available.
	
	MORE INFORMATION
	================
	
	When a DOD interface in RRAS attempts to dial a number, the status field will
	have a value of "Connecting." The static route that is used to activate the DOD
	is viewable by using the KERNROUT PRINT command.
	
	If the number that is dialed is not available, the DOD interface will be marked
	"Unreachable" only after it has failed all redial attempts. It will then stay
	unreachable for a default period of 10 minutes. The static route disappears from
	the routing table when the interface status is marked "Unreachable."
	
	After the wait interval, the status of the DOD interface will change to
	"Disconnected," at which point the DOD interface is available for use. When the
	status changes to "Disconnected," the static route in KERNROUT will reappear.
	
	If the DOD interface fails to connect again after this wait interval, it will
	then be marked "Unreachable" for a period of 20 minutes and, again, the static
	route will disappear from KERNROUT. Then, when the wait period is over, the
	status goes back to "Disconnected."
	
	This cycle continues in 10 minute intervals until 6 hours has been reached. The
	default maximum wait time remains at 6 hours until one of the following occurs:
	
	- A successful connection has been established [through either the wait
	  interval described here or manual dialing].
	
	  -or-
	
	- The router has been stopped and restarted.
	
	These default minimum and maximum times can be changed through the registry.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it. If
	you are running Windows NT, you should also update your Emergency Repair Disk
	(ERD).
	
	The 10-minute wait time is a default value that can be changed by adding the
	registry entry shown below:
	
	HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Router\Interfaces
	\<interface name>\MinUnreachabilityInterval
	
	REG_DWORD with a value in seconds
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	The MinUnreachabilityInterval is the smallest amount of time that the interface
	will stay "Unreachable" AND also defines what the wait interval is incremented
	by in next attempts.
	
	The maximum wait time is a default value that can be changed by adding the
	registry entry shown below:
	
	HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Router\Interfaces
	\<interface name>\MaxUnreachabilityInterval
	
	REG_DWORD with a value in seconds
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	The MaxUnreachabilityInterval is the highest wait time the DOD interface will
	stay "Unreachable" and RRAS will not increment above this wait time.
	
	
	Additional query words: ntrouter dial-on-demand static routes lost
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbwin2000ServSearch kbwin2000Search kbAudDeveloper kbWinAdvServSearch kbRRASNTSearch kbRRASNT400
	Version           : :2000,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
