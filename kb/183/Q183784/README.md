---
layout: page
title: "Q183784: FP: How to Use Hidden Fields in a Form With FrontPage"
permalink: /kb/183/Q183784/
---

## Q183784: FP: How to Use Hidden Fields in a Form With FrontPage

{% raw %}

	Article: Q183784
	Product(s): Word Front Page
	Version(s): MACINTOSH:1.0; WINDOWS:1.1,97
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 03-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows with Bonus Pack 
	- Microsoft FrontPage for Windows 1.1 
	- Microsoft FrontPage for the Macintosh, version 1.0 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 2002 version of this article, see Q292622.
	
	For a Microsoft FrontPage 2000 version of this article, see Q197741.
	
	For a Microsoft FrontPage 98 version of this article, see Q194074.
	
	SUMMARY
	=======
	
	This article describes how to use hidden fields in your forms.
	
	MORE INFORMATION
	================
	
	The Save Results Form Handler and the Registration Form Handler are both
	examples of form handlers. When a form is submitted in the browser, the values
	of each form field are passed to the form handler (specified by the action
	attribute of the <form> tag). For example, if your form field is a text
	box, the value sent to the form handler is the text entered in the text box.
	
	The values of each of the form fields between the <form> and </form>
	tags will be sent to the form handler. Not all form fields are visible however.
	Some form fields are hidden. Even so you can assign values to these hidden form
	fields and pass the values to the form handler.
	
	This can be especially useful when you have multiple forms saving results to a
	common e-mail address or results file. You could use a hidden field on each form
	that identifies the form by a unique number or name. The hidden fields in the
	form results would then indicate from which form the results came.
	
	To create hidden fields in your forms, follow these steps:
	
	1. Open the page that contains your form in FrontPage Editor.
	
	2. Right-click (Windows) or press CONTROL and click (Macintosh) a form field and
	  then click Form Properties on the menu that appears.
	
	3. Click Add.
	
	  a. In the Name box, type the name of the new hidden field.
	
	  b. In the Value box, type the value to be sent to the form handler.
	
	4. Click OK.
	
	5. On the File menu, click Save.
	
	Using Hidden Form Fields with the Save Results Form Handler
	-----------------------------------------------------------
	
	When using hidden forms with the Save Results Form Handler, the values of hidden
	fields will be saved to the results file (or e-mail message) the same way that
	values of other fields are.
	
	Hidden fields will be listed first in the results file (or e-mail message) in the
	order in which they appear in the Hidden Fields dialog box (Click Advanced in
	the Form Properties dialog box). When using a custom confirmation page, use the
	hidden field name in the Confirmation Fields section. >
	
	Using Hidden Form Fields with the Discussion Form Handler
	---------------------------------------------------------
	
	When using hidden forms with the Discussion Form Handler, the values of hidden
	fields are saved to the article the same way that the subject and contents
	fields are saved. Though when viewing the article, the hidden fields will be
	displayed at the top of the article above all other fields.
	
	Using Hidden Form Fields with the Registration Form Handler
	-----------------------------------------------------------
	
	You must take a few extra steps in order to save hidden fields using the
	Registration Form Handler:
	
	1. Right-click the form and then click Form Properties on the menu that appears.
	
	2. In the Form Properties dialog box, click Settings, and then click the
	  Advanced tab.
	
	3. In the Form Fields To Include box, type the hidden fields you want to save.
	
	4. Click OK in the Settings for Registration Form Handler dialog box.
	
	5. Click OK in the Form Properties dialog box.
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q143092 FP: How to Create a Registration Web
	
	  Q179188 FP98: [FrontPage Save Results Component] Shows Instead of Form
	
	  Q143090 FP: Overview of WebBot Components
	
	  Q177092 FP97: Overview of FrontPage Discussion Web Architecture
	
	  Q182123 FP: No Access to Form Properties by Right-Clicking Form Field
	
	  Q183049 FP98: Save Results Form Handler and Year 2000 Compliance Field
	
	Additional query words: 97
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbHWMAC kbOSMAC kbFrontPageSearch kbZNotKeyword8 kbFrontPage1xSearch kbFrontPage97Search kbFrontPageMac kbZNotKeyword3 kbFrontPage110
	Version           : MACINTOSH:1.0; WINDOWS:1.1,97
	Hardware          : MAC x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
