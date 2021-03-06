---
layout: page
title: "Q106480: BUG: Access Driver Returns Incorrect pcbValue"
permalink: /kb/106/Q106480/
---

## Q106480: BUG: Access Driver Returns Incorrect pcbValue

{% raw %}

	Article: Q106480
	Product(s): Open Database Connectivity (ODBC)
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): kbBug kbISS
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Open Database Connectivity, version 1.0 
	-------------------------------------------------------------------------------
	
	BUG# ODBCDBASE: 1858 (1.01.1928)
	
	SYMPTOMS
	========
	
	The ODBC Access driver returns incorrect pcbValue when a column with the ODBC
	SQL type SQL_TIMESTAMP is converted to SQL_C_DATE via SQLBindCol or SQLGetData.
	
	The following assumes that there is a table called DATETEST in which column
	number 2 is a column of type datetime:
	
	- SQLExecDirect the statement:
	
	  select * from DATETEST
	
	- Do a SQLBindCol on col #2 so that fCType is SQL_C_DATE.
	
	- Do a SQLFetch.
	
	- Examine the value of *pcbValue.
	
	It will be 10; while the expected =6.
	
	The same (invalid) pcbValue is returned if, instead of SQLBindCol, data is
	retrieved through SQLGetData with fCType = SQL_C_DATE.
	
	Correct pcbValue is returned when fCType = SQL_C_TIME.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Access Driver version
	1.01.1928. We are researching this problem and will post new information here in
	the Microsoft Knowledge Base as it becomes available.
	
	Additional query words: 1.01.1928
	
	======================================================================
	Keywords          : kbBug kbISS 
	Technology        : kbAudDeveloper kbODBCSearch kbODBC100
	Version           : WINDOWS:1.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
