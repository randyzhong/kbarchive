---
layout: page
title: "Q197134: WD97: Caption Numbers Reset When Caption Includes Chapter Number"
permalink: /kb/197/Q197134/
---

## Q197134: WD97: Caption Numbers Reset When Caption Includes Chapter Number

{% raw %}

	Article: Q197134
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta kbfield word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you insert a caption in a document that includes chapter numbering in the
	caption numbers, captions whose \r switches you modified are reset to 1.
	
	CAUSE
	=====
	
	When you select the Include Chapter Numbers option, Word replaces the existing
	captions with new ones, overwriting any changes you made to the SEQ fields in
	the captions.
	
	This behavior does not occur when the caption does not include the chapter
	number.
	
	Word does not put the \r switch in the first SEQ field for a caption sequence
	when including chapter numbers. Instead, Word adds the \s switch to the SEQ
	field to reset the sequence number. However, the \r switch can be added to the
	SEQ field in place of the \s switch to reset the sequence number of that caption
	sequence. If the \r switch is added, and another caption is inserted into that
	caption sequence, Word refreshes the caption sequence, removes the \r switch,
	and adds the \s switch back in.
	
	WORKAROUND
	==========
	
	To work around this situation, change the restart information only after all the
	captions have been inserted. To set or change a caption sequence starting
	number, follow these steps:
	
	1. On the Tools menu, click Options, and then click the View tab.
	
	2. Click to select the Field Codes check box, and then click OK.
	
	3. In the SEQ field, place the insertion point at the end of the field (to the
	  left of the closing field bracket) and replace \s 1 with "\r n" (without the
	  quotation marks), where "n" is the number you want to begin the sequence.
	
	Additional query words: figure equation table
	
	======================================================================
	Keywords          : kbdta kbfield word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
