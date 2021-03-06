---
layout: page
title: "Q195573: WD97: Word Doesn't Propose Correct &quot;Address To&quot;"
permalink: /kb/195/Q195573/
---

## Q195573: WD97: Word Doesn't Propose Correct &quot;Address To&quot;

{% raw %}

	Article: Q195573
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta kbenvelope winword word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When your document contains an address, Word may not properly identify the
	address paragraphs and may not propose the correct address information in the
	Address To box.
	
	CAUSE
	=====
	
	This problem may occur when you use one of the following commands:
	
	- The Envelopes And Labels command on the Tools menu
	
	  -or-
	
	- The ToolsCreateEnvelope macro command
	
	  -or-
	
	- The ToolsCreateLabel macro command
	
	MORE INFORMATION
	================
	
	When you use these commands in an open document, Word searches the document for
	an address, opens a dialog box with the proposed address, and allows you to
	print the address on an envelope or label. When Word conducts an address search,
	it uses the following rules:
	
	1. Word searches for any paragraphs that you defined as bookmarks named
	  "EnvelopeAddress" and "EnvelopeReturn."
	
	2. Word searches for highlighted paragraphs that represent each line of the
	  address.
	
	  NOTE: This will not work in Microsoft Word 97 for Windows if your address
	  lines end with line feeds rather than paragraph marks.
	
	3. Word searches for a series of paragraphs meeting the following criteria:
	
	  a. left-aligned
	
	  b. only include a few words
	
	  c. include three to five paragraphs in a row envelope address bookmark
	
	  d. no formatting between paragraphs
	
	If any of these conditions is not met, Word may return an unexpected result in
	the Address To box.
	
	NOTE: If you format an address as a single paragraph (for example, if you end
	each line with a new line character or SHIFT+ENTER), Word may not find the
	correct address information.
	
	Note also that if the first line of the address is formatted with space before or
	space after formatting, Word will not find the address. If you highlight the
	address, Word will show only the first line. This is true for the Labels dialog
	box as well as for the Envelope dialog box.
	
	Some third-party information managers, such as PackRat (for Windows), store
	addresses as one paragraph with line feeds (instead of carriage returns) at the
	end of each address line. In this situation, Word may not find the three to five
	consecutive paragraphs that satisfy its search algorithm. To work around this
	problem, replace the line feeds with carriage returns.
	
	If a single paragraph has more than 58 characters and spaces, Word may not find
	the correct address information.
	
	Additional query words: automatic block bookmark center centered delivery detect determine incorrect insert justified toolbar valid
	
	======================================================================
	Keywords          : kbdta kbenvelope winword word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
