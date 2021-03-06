---
layout: page
title: "Q169502: BUG: All Characters Following CHR(0) are Ignored with MSComm"
permalink: /kb/169/Q169502/
---

## Q169502: BUG: All Characters Following CHR(0) are Ignored with MSComm

{% raw %}

	Article: Q169502
	Product(s): Microsoft FoxPro
	Version(s): 5.0 5.0a
	Operating System(s): 
	Keyword(s): kbcode kbinterop kbvfp kbvfp500
	Last Modified: 30-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When an instance of the Microsoft Communication Control (MSComm Control)
	receives a CHR(0) it ignores that character and all characters that follow.
	
	RESOLUTION
	==========
	
	One of the following suggestions should resolve this problem:
	
	- Set the InputLen property of the Microsoft Communication Control to 1 and
	  read one character at a time.
	
	- If possible, do not send CHR(0) or NULL to the Microsoft Communication
	  control.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This has been corrected in Visual FoxPro 6.0.
	
	MORE INFORMATION
	================
	
	The Microsoft Communication Control truncates all characters following, and
	including, a CHR(0) or NULL that is passed to its Input. This occurs when the
	"NullDiscard" of the Microsoft Communication control set to ".F."
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Connect two computers via a NULL Modem cable. For example, COM1 port of a
	  computer (PC1) connected to the COM1 port of another computer (PC2) via a
	  Null Modem Cable.
	
	2. On PC1, place the following commands into a Visual FoxPro program and then
	  execute it, to create and run a form that sends serial output using the MS
	  Communication Control:
	
	  
	
	         OUTFORM = CreateObject("comtst1")
	         OUTFORM.Show
	         READ EVENTS
	
	         DEFINE CLASS COMTST1 AS FORM
	           Top = 7
	           Left = 88
	           Height = 239
	           Width = 288
	           DOCREATE = .T.
	           Caption = "Form1"
	           Name = "Form1"
	           OUTVAL = .F.
	           ADD OBJECT TEXT1 AS TEXTBOX WITH ;
	              HEIGHT = 37, ;
	              LEFT = 29, ;
	              TOP = 84, ;
	              WIDTH = 229, ;
	              Name = "Text1"
	           ADD OBJECT Olecontrol1 AS Olecontrol WITH ;
	              OLECLASS="MSCOMMLib.MSComm.1",;
	              TOP = 12, ;
	              LEFT = 0, ;
	              HEIGHT = 100, ;
	              WIDTH = 100, ;
	              NULLDISCARD = .F., ;
	              Name = "Olecontrol1"
	           ADD OBJECT Command1 AS CommandBUTTON WITH ;
	              TOP = 37, ;
	              LEFT = 104, ;
	              HEIGHT = 27, ;
	              WIDTH = 84, ;
	              CAPTION = "Open Port", ;
	              TABINDEX = 2, ;
	              Name = "Command1"
	           ADD OBJECT Command2 AS CommandBUTTON WITH ;
	              TOP = 133, ;
	              LEFT = 104, ;
	              HEIGHT = 27, ;
	              WIDTH = 84, ;
	              CAPTION = "Send", ;
	              Name = "Command2"
	           ADD OBJECT Command3 AS CommandBUTTON WITH ;
	              TOP = 193, ;
	              LEFT = 104, ;
	              HEIGHT = 27, ;
	              WIDTH = 84, ;
	              CAPTION = "Exit", ;
	              Name = "Command3"
	
	           PROCEDURE Command1.Click
	              IF This.CAPTION="Open Port"
	                 ThisForm.Olecontrol1.PORTOPEN=.T.
	                 This.Caption = "Close Port"
	              Else
	                 ThisForm.Olecontrol1.PORTOPEN=.F.
	                 This.Caption = "Open Port"
	              EndIf
	           ENDPROC
	
	           PROCEDURE Command2.Click
	              *** Send CHR() representation of numbers entered ***
	              OVAL1 = ALLTRIM(ThisForm.TEXT1.Value)
	              OVAL2 = "chr(" + STRTRAN(OVAL1, " ", ")+chr(") + ")"
	              ThisForm.Olecontrol1.OUTPUT=&OVAL2
	           ENDPROC
	
	           PROCEDURE Command3.Click
	              ThisForm.Release
	              CLEAR EVENTS
	           ENDPROC
	
	         ENDDEFINE
	
	3. Switch to PC2 and place the following code into a Visual FoxPro program and
	  execute it to create and run a form that receives serial input using the MS
	  Communication Control:
	
	  
	
	         INFORM = CREATEOBJECT("comtst2")
	         INFORM.SHOW
	         READ EVENTS
	
	         DEFINE CLASS comtst2 AS FORM
	             Top = 5
	             Left = 1
	             Height = 216
	             Width = 410
	             DoCreate = .T.
	             Caption = "Form1"
	             Name = "Form1"
	             inval1 = .F.
	             inval2 = .F.
	             ADD OBJECT Olecontrol1 AS OleCONTROL WITH ;
	                 OleCLASS="MSCOMMLib.MSComm.1",;
	                 TOP = 12, ;
	                 LEFT = 12, ;
	                 HEIGHT = 100, ;
	                 WIDTH = 100, ;
	                 NAME = "Olecontrol1", ;
	                 NullDiscard = .F., ;
	                 RThreshold = 10
	             ADD OBJECT Command1 AS CommandBUTTON WITH ;
	                 TOP = 24, ;
	                 LEFT = 150, ;
	                 HEIGHT = 27, ;
	                 WIDTH = 84, ;
	                 CAPTION = "Open Port", ;
	                 NAME = "Command1"
	             ADD OBJECT Edit1 AS EditBOX WITH ;
	                 FONTNAME = "Arial", ;
	                 HEIGHT = 64, ;
	                 LEFT = 24, ;
	                 TOP = 72, ;
	                 WIDTH = 252, ;
	                 NAME = "Edit1"
	             ADD OBJECT Command2 AS CommandBUTTON WITH ;
	                 TOP = 108, ;
	                 LEFT = 298, ;
	                 HEIGHT = 27, ;
	                 WIDTH = 84, ;
	                 CAPTION = "Clear Text", ;
	                 NAME = "Command2"
	             ADD OBJECT Command3 AS CommandBUTTON WITH ;
	                 TOP = 72, ;
	                 LEFT = 298, ;
	                 HEIGHT = 27, ;
	                 WIDTH = 84, ;
	                 CAPTION = "View Input", ;
	                 ENABLED = .F., ;
	                 NAME = "Command3"
	             ADD OBJECT Command4 AS CommandBUTTON WITH ;
	                 TOP = 178, ;
	                 LEFT = 150, ;
	                 HEIGHT = 27, ;
	                 WIDTH = 84, ;
	                 CAPTION = "Exit", ;
	                 NAME = "Command4"
	
	             PROCEDURE Command1.CLICK
	                 IF This.CAPTION="Open Port"
	                     ThisForm.Olecontrol1.portopen=.T.
	                     This.CAPTION = "Close Port"
	                     ThisForm.Command3.ENABLED=.T.
	                 ELSE
	                     ThisForm.Olecontrol1.portopen=.F.
	                     This.CAPTION = "Open Port"
	                     ThisForm.Command3.ENABLED=.F.
	                 ENDIF
	             ENDPROC
	
	             PROCEDURE Command2.CLICK
	                 ThisForm.Edit1.VALUE = ""
	             ENDPROC
	
	             PROCEDURE Command3.CLICK
	                 ThisForm.inval1 = ThisForm.Olecontrol1.INPUT
	                 FOR i = 1 TO LEN(ThisForm.inval1)
	                     ThisForm.inval2 = ASC(SUBSTR(ThisForm.inval1, i, 1))
	                     ThisForm.Edit1.VALUE=ThisForm.Edit1.VALUE+;
	                             " "+ALLTRIM(STR(ThisForm.inval2))+" "
	                 ENDFOR
	             ENDPROC
	
	             PROCEDURE Command4.CLICK
	                 ThisForm.RELEASE
	                 CLEAR EVENTS
	             ENDPROC
	
	         ENDDEFINE
	
	4. Click Open Port on the InForm form on PC2 to open the communication port on
	  that computer.
	
	5. Switch to PC1 and click Open Port on the OutForm form on PC1 to open the
	  communication port on that computer.
	
	6. Select the edit box on OutForm and enter the following numbers into the first
	  line:
	
	  
	
	        15 255 13 10 25
	
	  NOTE: Ensure that the numbers are entered with a space between them but with
	  no space before the first (15) and after the last number (25).
	
	7. Click SEND on OutForm to send the numbers.
	
	8. Switch to PC2 and click View Input on InForm. Look at the contents of the
	  edit box.
	
	  NOTE: The characters sent by OutForm are displayed in the edit box of InForm.
	  So, the characters are being received and recognized by MS Communication
	  Control on the receiving end.
	
	9. Click Clear Text to clear the edit box.
	
	10. Go back to PC1 and insert a "0" between the second and third number in the
	  edit box of OutForm so that the entries look like the following:
	
	  
	
	         15 255 0 13 10 25
	
	11. Click SEND on OutForm to send the numbers.
	
	12. Switch to PC1 and click View Input. Look at the contents of the edit box.
	
	  NOTE: Only the first and the second numbers (15 255), sent by OutForm on PC1,
	  are displayed in the edit box of InForm. The "0" and the numbers following
	  it are not displayed. This illustrates that after a receiving CHR(0) or NULL
	  that the MS Communication Control ignores that particular character and all
	  characters following it.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbinterop kbvfp kbvfp500 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : 5.0 5.0a
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
