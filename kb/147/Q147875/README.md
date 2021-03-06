---
layout: page
title: "Q147875: HOWTO: Use &quot;DSN-Less&quot; ODBC Connections with RDO and DAO"
permalink: /kb/147/Q147875/
---

## Q147875: HOWTO: Use &quot;DSN-Less&quot; ODBC Connections with RDO and DAO

{% raw %}

	Article: Q147875
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:1.5,2.0,2.1,2.5,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbRDO kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVBDB kbGrpDSMDAC kbDSupport kbGrpDSODBC
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Data Access Components versions 1.5, 2.0, 2.1, 2.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	With Microsoft Visual Basic versions 4.0, 5.0, and 6.0 for Windows, you can
	specify your ODBC (Open Database Connectivity) driver and server in your connect
	string when using RDO (Remote Data Object) and DAO (Data Access Objects) which
	eliminates the need to set up a DSN (Data Source Name). We call this a "DSN-
	Less" ODBC connection because you do not need to set up a DSN in order to access
	your ODBC database server.
	
	To do this, you specify a "driver=" and "server=" parameter in your connect
	string as in the following example:
	
	     cnstr = "driver={SQL Server};server=myserver;" & _
	       "database=mydb;uid=myuid;pwd=mypwd;dsn=;"
	     Set cn = en.OpenConnection("", False, False, cnstr)
	
	NOTE: The driver name must be surrounded by curly brackets. For example: "{SQL
	Server}."
	
	(CAUTION: DSN-Less connections will not work in Visual Basic 4.0 16-bit. If you
	try to use them you will get a General Protection Fault in module ODBC.DLL at
	0006:080F.)
	
	MORE INFORMATION
	================
	
	In Microsoft Visual Basic version 3.0 for Windows, you had to create a DSN that
	added an extra step when distributing your application because each workstation
	had to have the DSN created in order to access the specified server and
	database. This was done either manually with the ODBC Admin utility, through
	code with the RegisterDatabase function, or through code with the
	SQLConfigDatasource API function. For additional information on how to do this
	setup manually, please see the following articles in the Microsoft Knowledge
	Base:
	
	  Q123008 TITLE : How to Set Up ODBC Data Sources When Distributing an App
	
	  Q126940 : RegisterDatabase Fails After ODBC Version 2.x Installed
	
	  Q132329 : RegisterDatabase Method Does Not Modify ODBC.INI File
	
	Sample Program
	--------------
	
	The following RDO example uses a "DSN-less" ODBC connection so you do not need to
	set up a DSN with the ODBC Admin utility beforehand.
	
	1. Start a new project in Visual Basic. Form1 is created by default.
	
	2. Add a command button to Form1, Command1 by default.
	
	3. Paste the following code into the General Declarations section of Form1:
	
	        Dim en As rdoEnvironment
	        Dim cn As rdoConnection
	
	        Private Sub Form_Load()
	          MousePointer = vbHourglass
	          Dim strConnect As String
	          ' Change the next line to reflect your driver and server.
	          strConnect = "driver={SQL Server};server=jonfo5;" & _
	            "database=pubs;uid=sa;pwd="
	          Set en = rdoEngine.rdoEnvironments(0)
	          Set cn = en.OpenConnection( _
	            dsName:="", _
	            Prompt:=rdDriverNoPrompt, _
	            ReadOnly:=False, _
	            Connect:=strConnect)
	          cn.QueryTimeout = 600
	          MousePointer = vbNormal
	        End Sub
	        Private Sub Command1_Click()
	          MousePointer = vbHourglass
	          Dim rs As rdoResultset
	          Set rs = cn.OpenResultset(Name:="Select * from authors", _
	            Type:=rdOpenForwardOnly, _
	            LockType:=rdConcurReadOnly, _
	            Options:=rdExecDirect)
	          Debug.Print rs(0), rs(1), rs(2)
	          MousePointer = vbNormal
	        End Sub
	
	4. Note that you must change your DRIVER, SERVER, DATABASE, UID, and PWD
	  parameters in the OpenConnection method. You also need to modify the SQL
	  statement contained in the Command1_Click event to match your own SQL data
	  source.
	
	5. Check the Microsoft Remote Data Object in the Project References.
	
	6. Start the program or press the F5 key.
	
	7. Click the Command1 button to create a rdoResultset and display the first row
	  of data in the debug window.
	
	REFERENCES
	==========
	
	Hitchhiker's Guide to Visual Basic and SQL Server, Microsoft Press.
	ISBN: 1-55615-906-4.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbRDO kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVBDB kbGrpDSMDAC kbDSupport kbGrpDSODBC 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbMDACSearch kbVB400Search kbVB400 kbMDAC150 kbMDAC200 kbMDAC210 kbMDAC250
	Version           : WINDOWS:1.5,2.0,2.1,2.5,4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
