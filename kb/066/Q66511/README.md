---
layout: page
title: "Q66511: SHARE Does Not Need to Be Loaded in MS-DOS 5.0 or Later"
permalink: /kb/066/Q66511/
---

## Q66511: SHARE Does Not Need to Be Loaded in MS-DOS 5.0 or Later

{% raw %}

	Article: Q66511
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	MS-DOS 4.x requires that SHARE.EXE be loaded on systems with logical drives
	larger than 32 megabytes (MB). This is not required for MS-DOS versions 5.0 and
	later.
	
	The file control block (FCB) file-access method assumes 32 MB or smaller logical
	drives. In MS-DOS version 4.x, SHARE.EXE is loaded to change any attempted FCB
	file accesses into File Handle file accesses on large logical drives. Without
	SHARE.EXE, applications that attempt FCB file accesses fail. In MS-DOS versions
	5.0 and later, translating FCB file accesses to File Handle accesses is
	performed by the MS-DOS kernel; therefore, loading SHARE.EXE is not necessary.
	
	Additional query words: 6.22 5.00 5.00a 6.00 6.20 share
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
