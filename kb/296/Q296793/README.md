---
layout: page
title: "Q296793: MCSE Training Kit Microsoft SQL Server 2000 System Administratio"
permalink: /kb/296/Q296793/
---

## Q296793: MCSE Training Kit Microsoft SQL Server 2000 System Administratio

{% raw %}

	Article: Q296793
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 02-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS MCSE Training Kit, Microsoft SQL Server 2000 System Administration ISBN 0-7356-1247-1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains comments, corrections, and information about known errors
	relating to the Microsoft Press book MCSE Training Kit Microsoft SQL Server 2000
	System Administration, ISBN 0-7356-1247-1.
	
	The following topics are covered:
	
	- Page 56: Corrections To Steps 25 And 26
	
	- Page 56: Correction To Path
	
	- Page 124: Correction To Uniform Extents Description
	
	- Page 139: "GET DATE" Should Be "GETDATE"
	
	- Page 140: SpacedUsed Should Be SpaceUsed
	
	- Page 156: Incorrect Log File Extension
	
	- Page 163: Incorrect System Function
	
	- Page 558: Publisher Should Be Distributor
	
	MORE INFORMATION
	================
	
	Page 56: Corrections To Steps 25 And 26
	---------------------------------------
	
	On page 56, change:
	"25. Click Start and then click Run.
	The Open dialog box appears.
	
	26. In the Open drop-down combo box, type..."
	
	To:
	"25. Click Start, point to Accessories, then click Command Prompt.
	The Command Prompt window appears.
	
	26. At the command prompt, type..."
	
	
	Page 56: Correction To Path
	---------------------------
	
	On page 56,
	
	Change:
	"26. ... d:\x86\setup\setupsql.exe k=SMS -s -m -SMS -f1 'c:\winnt\setup.iss'.
	
	27. Click OK."
	
	To:
	"26. ... d:\sqleval\x86\setup\setupsql.exe k=SMS -s -m -SMS -f1
	'c:\winnt\setup.iss'.
	
	27. Press Enter."
	
	
	Page 124: Correction To Uniform Extents Description
	---------------------------------------------------
	
	On page 124, in the first paragraph under "Allocating Space for Tables and
	Indexes",
	
	Change:
	"... and uses uniform extents to store, whereas SQL Server 2000 uses uniform
	extents to store data from a single object."
	
	To:
	"... and uses uniform extents to store data from a single object."
	
	
	Page 139: "GET DATE" Should Be "GETDATE"
	----------------------------------------
	
	On page 139, in Table 5.4, the system function "GETDATE" should be one word, with
	no space in it.
	
	Change:
	"GET DATE()"
	
	To:
	"GETDATE()"
	
	
	Page 140: SpacedUsed Should Be SpaceUsed
	----------------------------------------
	
	On page 140, in step 7,
	
	Change:
	"SpacedUsed"
	
	To:
	"SpaceUsed"
	
	
	Page 156: Incorrect Log File Extension
	--------------------------------------
	
	On page 156, in the code sample,
	
	Change:
	"TSQLDB2.ledf"
	
	To:
	"TSQLDB2.ldf"
	
	
	Page 163: Incorrect System Function
	-----------------------------------
	
	On page 163, in the first paragraph, change:
	"DATAPROPERTYEX"
	
	To:
	"DATABASEPROPERTYEX"
	
	
	Page 558: Publisher Should Be Distributor
	-----------------------------------------
	
	On page 558, in the first line,
	
	Change:
	"By default, this agent runs at the Publisher, using the server resources of the
	Publisher."
	
	To:
	"By default, this agent runs at the Distributor, using the resources of the
	Distributor."
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: TKBOOK 0-7356-1247-1 RABELER
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
