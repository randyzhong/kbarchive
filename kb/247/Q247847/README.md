---
layout: page
title: "Q247847: XCLN: Creating a Rule to Process Mail Sent on Behalf of Another"
permalink: /kb/247/Q247847/
---

## Q247847: XCLN: Creating a Rule to Process Mail Sent on Behalf of Another

{% raw %}

	Article: Q247847
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:2000,97,98
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook 2000 
	- Microsoft Outlook 97 
	- Microsoft Outlook 98 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Outlook 97, Outlook 98, and Outlook 2000, the Rules wizard does not allow you
	to move (or in any way process) a mail item that was sent on behalf of another
	user. To create such a rule, you need to use custom forms and rules based on
	categories.
	
	MORE INFORMATION
	================
	
	Microsoft Exchange Server gives you the ability to send mail on behalf of
	another user. This is done by giving the appropriate permission in the Microsoft
	Exchange Server Administrator program. For additional information on how to do
	so, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q234696 XCLN: How to Set Up 'Send on Behalf Of' Permissions
	
	For example, if a user called USER1 has been given such rights for USER2, then
	USER1 can send a message on behalf of USER2. If you want to create a rule such
	that all messages sent by USER1 on behalf of USER2 are moved to a folder called
	Sent On Behalf Of USER2, nothing in the Rules wizard lets you do that.
	
	One solution is to create a custom form that will be preset to a category called
	"Sent On Behalf Of." In this example, USER1 can use this form whenever he or she
	sends mail on behalf of USER2. You can then create a rule that checks messages
	after they are sent, checks if the category is set to Sent On Behalf Of and, if
	so, moves those messages to a specific folder (or processes those messages in
	other ways).
	
	The detailed steps are given below. These steps are for Outlook 97, but the same
	steps apply, with minor differences, for Outlook 98 and Outlook 2000. To create
	a form:
	
	1. In Outlook 97, open a new message form.
	
	2. On the Edit menu, click Categories.
	
	3. Add a category called "Sent On Behalf Of," and then click OK.
	
	4. On the Tools menu, click Design Outlook Form.
	
	5. On the File menu, click Publish Form As.
	
	6. Give a name to the form (for example, SentOnBehalfOf).
	
	7. Click Publish. By default, the form is published in the Personal Forms
	  Library.
	
	8. On the File menu, click Close. Click No, when you are prompted to save
	  changes.
	
	To create a rule:
	
	1. On the Tools menu, click Rules Wizard, and then click New.
	
	2. Click the "When I send a message" radio button, and then click Next.
	
	3. In the "Which conditions do you want to check" box, click Assigned To
	  Category.
	
	4. In the Rule description box, click Category.
	
	5. Type "Sent On Behalf Of" (without the quotation marks), click OK, and then
	  click Next.
	
	6. Click "Move a copy to the Specified Folder".
	
	7. In the Rule description box, click Specified.
	
	8. Choose the folder to which you want the message to be moved.
	
	9. Click OK, and then click Next.
	
	10. Click Next, click Finish, and then click OK twice.
	
	NOTE: The procedure shows one of the several ways in which a category may be used
	to filter mail. There are several other ways. Which method you use depends on
	the objective you want to achieve and the peculiarities and limitations of your
	environment.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbOutlook2000Search kbOutlook97Search kbOutlook98Search kbZNotKeyword3
	Version           : WINDOWS:2000,97,98
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
