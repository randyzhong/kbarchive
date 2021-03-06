---
layout: page
title: "Q307813: SMS: Systems Management Server and Storage Area Network"
permalink: /kb/307/Q307813/
---

## Q307813: SMS: Systems Management Server and Storage Area Network

{% raw %}

	Article: Q307813
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3,2.0 SP4
	Operating System(s): 
	Keyword(s): kbsms200
	Last Modified: 25-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3, 2.0 SP4 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Systems Management Server (SMS) is designed to work with any hardware that is
	certified on the Windows Hardware Compatibility List for Microsoft Windows NT
	and Microsoft Windows 2000-based computers. For more information about the
	Windows Hardware Compatibility List, view the following Microsoft Web site:
	
	  http://www.microsoft.com/hcl
	
	Note, however, that SMS 2.0 has not been tested with all hardware configurations
	that are listed on the HCL and you may experience issues with some
	configurations.
	
	Storage Area Networks (SAN) configurations are fully supported by SMS, but have
	not been specifically tested with SMS. Microsoft supports placing SMS data
	stores on either direct-attached storage or on SAN-attached storage. Note that
	this is subject to a maximum limit of 4 terabytes (TB) for each volume.
	
	MORE INFORMATION
	================
	
	Some storage vendors offer optional features such as additional mirrors, mirror
	splitting, or remote replication (synchronous or asynchronous). Microsoft has
	not tested SMS with these features and you should consult with your storage
	vendor to ensure compatibility and to prevent data loss. Microsoft provides
	commercially feasible support for using SMS with these optional features. In
	addition, where you use Microsoft SQL Server as the underlying data store, you
	must insure that any storage software or optional hardware feature is also
	compatible with SQL. If a problem occurs, you may need to reconfigure a site
	system to use storage that is not SAN-based to isolate and correct the problem.
	
	You should consider all risks when you choose any configuration. Although no
	known problem with a SAN configuration and SMS has been reported, it is
	important to note that there is a reduced level of testing that has been
	performed by Microsoft with SMS in this configuration.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3 kbSMS200SP4
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3,2.0 SP4
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
