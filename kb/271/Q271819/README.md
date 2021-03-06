---
layout: page
title: "Q271819: HOWTO: Spell Check in Visual FoxPro with Microsoft Wor"
permalink: /kb/271/Q271819/
---

## Q271819: HOWTO: Spell Check in Visual FoxPro with Microsoft Wor

{% raw %}

	Article: Q271819
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2000,3.0,3.0b,5.0,5.0a,6.0,97
	Operating System(s): 
	Keyword(s): kbCOMt kbOOP kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport kbWord97 kbword2000 kbCo
	Last Modified: 12-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Often, developers want to incorporate spell checking functionality into their
	Visual FoxPro (VFP) applications. While Visual FoxPro includes its own spell
	checking (in the form of SPELLCHK.APP), this component cannot be redistributed.
	
	A number of third-party spell checking solutions exist for Visual FoxPro (see the
	"References" section later in this article). However, if the end-user of the VFP
	application has Microsoft Word 97 or Microsoft Word 2000, the VFP application
	can take advantage of Word to do its spell checking.
	
	MORE INFORMATION
	================
	
	The following Visual FoxPro code demonstrates the use of Microsoft Word to spell
	check some text. To use it, save the code to a new program and run it in
	Microsoft Visual FoxPro.
	
	With the form running, note that there is misspelled text in the edit box. When
	you click the Check Spelling command button, code runs that first checks for the
	existence of Microsoft Word, and then uses Word to check the text in the edit
	box (if it is installed). Subsequent clicks of the command button do not start
	more instances of Word (the initial instance is used until the form is
	released), and a message box appears if there are no spelling mistakes.
	
	  *!*********** START CODE ***********
	  PUBLIC oform1
	
	  oform1=CREATEOBJECT("form1")
	  oform1.Show
	  RETURN
	
	  *************************************************
	  *
	  *
	  DEFINE CLASS form1 AS form
	
	  	Height = 250
	  	Width = 375
	  	ShowWindow = 2
	  	AutoCenter = .T.
	  	BorderStyle = 2
	  	Caption = "VFP/Word Spell Checking"
	  	MaxButton = .F.
	  	Name = "Form1"
	
	  	ADD OBJECT edttexttocheck AS editbox WITH ;
	  		Height = 163, ;
	  		Left = 23, ;
	  		Top = 21, ;
	  		Width = 332, ;
	  		Name = "edtTextToCheck"
	
	  	ADD OBJECT cmdcheckspelling AS commandbutton WITH ;
	  		Top = 207, ;
	  		Left = 115, ;
	  		Height = 27, ;
	  		Width = 149, ;
	  		Caption = "\<Check Spelling", ;
	  		Name = "cmdCheckSpelling"
	
	  	PROCEDURE findword
	  		*~~~~~~~~~~~~~~~~~~~~~
	  		* PROCEDURE FindWord
	  		*
	  		* AUTHOR: Trevor Hancock, , Microsoft Corporation
	  		* CREATED : 08/22/00 11:50:32 AM
	  		*
	  		* ABSTRACT: Locates an installation of MS Word using the FindExecutable API
	  		*                 Creates a file with a .doc extension, checks the association on that
	  		*                 file using FindExecutable, then deletes the file. FindExecutable returns
	  		*                 the full, null terminated path to the application associated with
	  		*                 .doc files (in this case).
	  		* ACCEPTS: Nothing
	  		* RETURNS: Full path to the application associated with .doc files on this machine.
	  		*~~~~~~~~~~~~~~~~~~~~~
	
	  		LOCAL lcPath, lcResult, lcFileName, llRetVal, ;
	  			lcCurDir, lnFileHand, lcWordPath
	
	  		lcPath = SPACE(0)
	  		lcResult = SPACE(128)
	  		llRetVal = .F.
	  		*!* Determine the DIR this form is running from. JUSTPATH() and ADDBS()
	  		*!* could be used here instead (if using VFP6), but this code will work in any VFP version.
	  		lcCurDir = SUBSTR(SYS(16,0),ATC([ ],SYS(16,0),2)+1)
	  		lcCurDir = SUBSTR(lcCurDir,1,RAT([\],lcCurDir))
	
	  		lcFileName = lcCurDir + SYS(3) + [.doc]
	
	  		*!* Create a file with a .doc extension.
	  		*!* Could use STRTOFILE() here in VFP6.
	  		lnFileHand = FCREATE(lcFileName,0)
	  		= FCLOSE(lnFileHand)
	
	  		DECLARE INTEGER FindExecutable IN shell32 STRING @lcFilename, ;
	  			STRING @lcPath , STRING @lcResult
	
	  		*!* Determine the file association on .DOC files
	  		IF FindExecutable(@lcFileName, @lcPath, @lcResult) > 32
	  		*!* Strip off trailing chr(0)
	  			lcWordPath = UPPER(SUBSTR(lcResult,1,LEN(ALLTR(lcResult))-1))
	  			IF [WINWORD] $ lcWordPath
	  				llRetVal = .T.
	  			ENDIF
	  		ENDIF
	  		*!* Clean up after ourselves
	  		ERASE (lcFileName)
	  		RETURN llRetVal
	  	ENDPROC
	
	  	PROCEDURE Destroy
	  		IF TYPE([goWord]) = [O]
	  			IF TYPE([goWordDoc]) = [O]
	  				goWordDoc.SAVED = .T.
	  				goWordDoc.CLOSE
	  			ENDIF
	  			goWord.QUIT
	  		ENDIF
	  		RELEASE goWord, goWordDoc
	  	ENDPROC
	
	  	PROCEDURE Init
	  		THIS.edtTextToCheck.VALUE = "Thhis text has mistakees in it. We will seend " +  ;
	  			"it to Word and have it cheked."
	
	  	ENDPROC
	
	  	PROCEDURE cmdcheckspelling.Click
	  		*~~~~~~~~~~~~~~~~~~~~~
	  		* PROCEDURE cmdcheckspelling.CheckSpelling
	  		*
	  		* AUTHOR: Trevor Hancock, Microsoft Corporation
	  		* CREATED : 08/22/00 12:03:46 PM
	  		*
	  		* ABSTRACT: Automates MS Word to check the spelling of text in
	  		*                 THISFORM.edtTextToCheck
	  		* ACCEPTS: Nothing
	  		* RETURNS: Nothing
	  		*~~~~~~~~~~~~~~~~~~~~~
	
	  		IF TYPE([goWord]) # [O]	&& Check if you have already instantiated Word
	
	  			IF !THISFORM.FindWord()	&& You don't have Word up, so let's locate it.
	  				MESSAGEBOX([Microsoft Word is either not installed or is incorrectly registered.], + ;
	  					0,[Word Start-Up Failed])
	  				RETURN .F.
	  			ENDIF
	
	  			*!* Change the mouse pointer for all form controls to indicate processing (opening Word)
	  			WITH THISFORM
	  				.cmdCheckSpelling.MOUSEPOINTER = 11
	  				.edtTextToCheck.MOUSEPOINTER = 11
	  				.MOUSEPOINTER = 11
	  			ENDWITH
	
	  			PUBLIC goWord, goWordDoc	&& Public vars for Word and Document1 in Word.
	  			goWord = CREATEOBJECT([WORD.APPLICATION])	&& Create Word
	  			WITH goWord
	  				.WINDOWSTATE= 0  && wdWindowStateNormal (needs to be Normal before you can move it)
	  				.MOVE(1000,1000)	&& Move the window out of view
	  				goWordDoc = .Documents.ADD
	  			ENDWITH
	
	  			*!* Change mouse pointers back
	  			WITH THISFORM
	  				.cmdCheckSpelling.MOUSEPOINTER = 0
	  				.edtTextToCheck.MOUSEPOINTER = 0
	  				.MOUSEPOINTER = 0
	  			ENDWITH
	
	  		ENDIF
	
	  		WITH goWordDoc
	  			.Content.TEXT = ALLTRIM(THISFORM.edtTextToCheck.VALUE)
	  			.ACTIVATE
	  			IF .SpellingErrors.COUNT > 0
	  				.CHECKSPELLING
	  			ELSE
	  				=MESSAGEBOX([Spell check complete. No errors found],0,[Spell Check])
	  			ENDIF
	  			*!* For some reason, Word likes to make itself visible here. Keep it hidden...
	  			goWord.VISIBLE = .F.
	  			THISFORM.edtTextToCheck.VALUE = .Content.TEXT
	  		ENDWITH
	  	ENDPROC
	
	  ENDDEFINE
	  *
	  *
	  **************************************************
	  *!*********** END CODE ***********
	
	REFERENCES
	==========
	
	For additional information on spell checking with Microsoft Visual FoxPro, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q175620 INFO: Limitations on Distribution of Spellchk.app
	
	Some third-party spell checking options for Visual FoxPro are:
	
	  Escribe Spell Checker for FoxPro from Hallogram Publishing
	  http://www.hallogram.com/speller/
	
	  Polar SpellChecker Component
	  http://www.hallogram.com/polarspell/index.html
	
	  VideoSoft vsSPELL
	  http://www.hallogram.com/videosoft/vsspell/index.html
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by Trevor
	Hancock, Microsoft Corporation.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCOMt kbOOP kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport kbWord97 kbword2000 kbCodeSnippet 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:2000,3.0,3.0b,5.0,5.0a,6.0,97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
