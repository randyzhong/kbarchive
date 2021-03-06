---
layout: page
title: "Q143033: INFO: Comparing AbsolutePosition to PercentPosition in VB"
permalink: /kb/143/Q143033/
---

## Q143033: INFO: Comparing AbsolutePosition to PercentPosition in VB

{% raw %}

	Article: Q143033
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Microsoft Visual Basic 4.0 using Jet's DAO model, there are two Properties
	that can help you determine the current cursor position or that you can use to
	set the cursor to a certain position.
	
	This article will demonstrate both properties and give you some ideas on when to
	use one or the other.
	
	MORE INFORMATION
	================
	
	According information from the online Help, the description of the
	AbsolutePosition is as follows:
	
	Returns or sets the relative record number of a Recordset object's current
	record. Applies to the Recordset Object as a Dynaset-type or Snapshot-
	type(except for forward-only Snapshots and passthrough queries).
	
	According information from the online Help, the description of the
	PercentPosition is as follows:
	
	Returns or sets a value that indicates or changes the approximate location of the
	current record in the Recordset object based on a percentage of the records in
	the Recordset. Applies to all three types of Recordset Objects (except for
	forward-only Snapshots and passthrough queries).
	
	In the following code, I use the rs.MoveLast method before referring to
	rs.PercentPosition. This is because PercentPosition is dependent on RecordCount,
	and AbsolutePosition is not. The RecordCount property is not accurate until you
	move to the end of your Recordset object. Also keep in mind that RecordCount is
	not always 100 percent accurate, it is just an estimate of the number of rows in
	your recordset, and therefore PercentPosition is not always accurate--but
	AbsolutePosition is always accurate. For instance, a dynaset in a multi-user
	environment does not reflect rows other users have added until you issue the
	refresh method.
	
	
	Step-by-Step Example
	--------------------
	
	1. Start Visual Basic or from the File menu, choose New Project (ALT, F, N) if
	  Visual Basic is already running. Form1 is created by default.
	
	2. Add two Command buttons(Command1, Command2), four Labels (Label1, Label2,
	  Label3, Label4), one Data Control(Data1) and one Text box(Text1) to Form1.
	  Place Label1 to the left of Text1 and place Label2 next to the Data control.
	  Place Label3 next to the Command1 button and place Label4 next to the
	  Command2 button.
	
	3. Set the following properties for each control:
	
	  Default   Property        Set to
	  -----------------------------------------------
	  Command1   Caption        AbsolutePosition
	  Command2   Caption        PercentPosition
	  Data1      DatabaseName   BIBLIO.MDB
	  Data1      RecordSource   Titles
	  Label1     Caption        Enter a Number:
	  Text1      Text
	  Label2     Caption
	  Label2     DataSource     Data1
	  Label2     DataField      Title
	  Label3     Caption
	  Label4     Caption
	
	4. Add the following code to the Command1_Click event:
	
	     Private Sub Command1_Click()
	       Dim rs1 As Recordset
	       Set rs1 = Data1.Recordset
	       rs1.MoveLast
	       rs1.AbsolutePosition = Val(Text1.Text)
	       Label3.Caption = "Absolute Results: " & rs1("title")
	     End Sub
	
	5. Add the following code to the Command2_Click event:
	
	     Private Sub Command2_Click()
	       Dim rs2 As Recordset
	       Set rs2 = Data1.Recordset
	       rs2.MoveLast    'RecordCount now accurate
	       rs2.PercentPosition = Val(Text1.Text)
	       Label4.Caption = "Percent Results: " & rs2("title")
	     End Sub
	
	6. From the Run menu, choose Start (ALT, R, S), or press the F5 key to run the
	  program. Enter a number from 1 to 100 into Text1. Press the Command1 button,
	  then press the Command2 button. Look at the different results in Label3
	  versus Label4. You can test the location by selecting the arrow keys of the
	  Data control also.
	
	  You can experiment with different numbers to get different results. The
	  PercentPosition property is good for helping in displaying a status bar type
	  of indicator. The AbsolutePosition property could be used as a reference for
	  jumping to certain records, but you could use a BookMark as well.
	
	Additional query words: kbVBp400 kbVBp600 kbdse kbDSupport kbVBp
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600 kbVB400Search kbVB400
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
