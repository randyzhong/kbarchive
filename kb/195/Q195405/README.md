---
layout: page
title: "Q195405: FIX: Corrupt Record Added in Grid Using View with Default Value"
permalink: /kb/195/Q195405/
---

## Q195405: FIX: Corrupt Record Added in Grid Using View with Default Value

{% raw %}

	Article: Q195405
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b,5.0,5.0a
	Operating System(s): 
	Keyword(s): kbDatabase kbvfp300bBUG kbvfp500aBUG kbvfp600fix KbDBFDBC
	Last Modified: 10-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Use a grid control, which has a local view as its RecordSource. When the base
	table for the view calls a function for default value of its key field, if you
	repeatedly add records to the view, and set focus to the grid each time a record
	is added to force the grid to refresh, you may find a corrupt extra record added
	to the view. The corrupted record contains nulls (ASCII 0 characters) or spaces.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been corrected in Visual FoxPro 6.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. To create the data, run the following code from a program (.prg) file. This
	  program makes a DBC, a table, and a local view based on the table.
	
	        CLOSE DATA ALL
	        CREATE DATABASE 'TESTDB.DBC'
	
	        CREATE TABLE 'testtab' NAME 'testtab' ;
	           (PK C(5) NOT NULL DEFAULT newid(), ;
	           F1 C(5) NOT NULL)
	
	        CREATE SQL VIEW "v_testtab" ;
	            AS SELECT * FROM testdb!testtab
	
	        =DBSetProp('V_TESTTAB', 'View', 'UpdateType', 2)
	        =DBSetProp('V_TESTTAB', 'View', 'WhereType', 3)
	        =DBSetProp('V_TESTTAB', 'View', 'SendUpdates', .T.)
	        =DBSetProp('V_TESTTAB', 'View', 'Tables', 'testdb!testtab')
	        =DBSetProp('V_TESTTAB.pk', 'Field', 'KeyField', .T.)
	        =DBSetProp('V_TESTTAB.pk', 'Field', 'Updatable', .F.)
	        =DBSetProp('V_TESTTAB.pk', 'Field', 'UpdateName',
	        'testdb!testtab.pk')
	        =DBSetProp('V_TESTTAB.pk', 'Field', 'DataType', "C(5)")
	        =DBSetProp('V_TESTTAB.f1', 'Field', 'KeyField', .F.)
	        =DBSetProp('V_TESTTAB.f1', 'Field', 'Updatable', .T.)
	        =DBSetProp('V_TESTTAB.f1', 'Field', 'UpdateName',
	        'testdb!testtab.f1')
	        =DBSetProp('V_TESTTAB.f1', 'Field', 'DataType', "C(5)")
	
	2. To demonstrate the behavior, run the following code from a program (.prg)
	  file:
	
	        * Set the number of iterations
	        #DEFINE NREPS 100
	        SET ASSERT ON
	        PUBLIC oform1
	        SET MULTILOCKS ON
	        CLOSE DATABASE ALL
	        * Open the view
	        USE testdb!v_testtab
	        * Set the buffering
	        =CURSORSETPROP('buffering',5,'v_testtab')
	        =CURSORSETPROP('buffering',1,'testtab')
	        oform1=CREATEOBJECT("form1")
	        oform1.SHOW
	        RETURN
	
	        DEFINE CLASS form1 AS FORM
	           CAPTION = "Form1"
	
	        ADD OBJECT cmdbase1 AS COMMANDBUTTON WITH ;
	           TOP = 214, ;
	           LEFT = 146, ;
	           HEIGHT = 27, ;
	           CAPTION = "Run Test", ;
	           NAME = "Cmdbase1"
	
	        ADD OBJECT grid1 AS GRID WITH ;
	           HEIGHT = 182, ;
	           LEFT = 25, ;
	           RECORDSOURCE = "v_testtab", ;
	           TOP = 24
	
	        PROCEDURE cmdbase1.CLICK
	           LOCAL lnSelectedTab,lcGridAlias, lnCount, lnCnt, lni, retval, ;
	           lnCnt2
	           FOR lnCount=1 TO NREPS
	              lnSelectedTab=SELECT()
	              SELECT v_testtab
	              lnCnt=RECCOUNT('v_testtab')
	              FOR lni = 1 TO 5
	                 APPEND BLANK
	                 REPLACE f1 WITH SUBSTR(SYS(3),4,5)
	                 * Remove the following line and the error goes away
	                 THISFORM.grid1.SETFOCUS()
	              ENDFOR
	              lncnt2 = RECCOUNT('v_testtab')
	              SELECT v_testtab
	              retval1=TABLEUPDATE(.T.)
	              * Compare RECCOUNT of view to RECCOUNT before TABLEUPDATE().
	              * If they disagree, the behavior has occurred.
	              ASSERT RECCOUNT('v_testtab')=lnCnt2 MESSAGE ;
	                 'Changed after update'
	              SELECT (lnSelectedTab)
	              * Works with setfocus here instead
	              * thisform.grid1.setfocus()
	           ENDFOR
	          ENDPROC
	        ENDDEFINE
	
	        * Generic Newid function to make new ID values.
	        FUNCTION NewID()
	           LOCAL lcAlias, lnLastID, lcOldReprocess, lnOldArea
	           lnOldArea = SELECT()
	           lcAlias = UPPER(ALIAS())
	           lcOldReprocess = SET('REPROCESS')
	           SET REPROCESS TO AUTOMATIC
	            IF USED('IDTable')
	              SELECT IDTable
	            ELSE
	              SELECT 0
	              IF FILE('IDTable.dbf')
	                 USE IDTable
	              ELSE
	                 CREATE TABLE IDTable (TableAlias c(50), LastID N(10))
	                 INDEX ON UPPER(TableAlias) TAG TableAlias
	              ENDIF
	           ENDIF
	
	        LOCATE FOR ALLT(UPPER(lcAlias))==ALLT(UPPE(TableAlias))
	        IF !FOUND()
	           APPEND BLANK
	           REPLACE TableAlias WITH UPPER(lcAlias)
	           REPLACE LastID WITH 0
	        ENDIF
	        IF RLOCK()
	           REPLACE IDTable.LastID WITH IDTable.LastID + 1
	           lnLastID = IDTable.LastID
	           UNLOCK
	        ENDIF
	           SELECT (lnOldArea)
	           SET REPROCESS TO lcOldReprocess
	           RETURN PADL(ALLT(STR(lnLastID)),5,'0')
	        ENDFUNC
	
	3. Click the Run Test command button.
	
	4. When the view record count changes after the TABLEUPDATE(), the assert dialog
	  box is displays. This indicates the corruption occurred. Press the Cancel
	  button in the assert dialog box. If you have difficulty reproducing this, you
	  may need to increase the iterations by changing the 100 in the line #DEFINE
	  NREPS 100 to a larger number like 150 or 200.
	
	Look at the last record in the grid. There will be a record under the record
	where the highlight appears. The extra record contains ASCII 0 characters, and
	may appear as square boxes or vertical bars. You may have to scroll the grid by
	clicking the grid's vertical scrollbars down arrow once to make the extra record
	visible.
	
	If you remove or comment the first THISFORM.grid1.SETFOCUS() line in the
	cmdbase1.CLICK procedure, and uncomment the second SETFOCUS line near the end of
	the same procedure, the extra record is not added.
	
	If you modify the view, and place the Default Value on the view field as well as
	the base table field, and then make the view field updateable, the extra record
	will is not added.
	
	REFERENCES
	==========
	
	(c) Microsoft Corporation 1998. All Rights Reserved. Contributions by Jim
	Saunders, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDatabase kbvfp300bBUG kbvfp500aBUG kbvfp600fix KbDBFDBC 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP500a
	Version           : WINDOWS:3.0,3.0b,5.0,5.0a
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
