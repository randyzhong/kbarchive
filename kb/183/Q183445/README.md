---
layout: page
title: "Q183445: Etk50pid.exe Incorrect Product ID Displayed in About Box"
permalink: /kb/183/Q183445/
---

## Q183445: Etk50pid.exe Incorrect Product ID Displayed in About Box

{% raw %}

	Article: Q183445
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbfile kbpatch kbOAK kbOSWinCE200
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows CE Embedded Toolkit for Visual C++ 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Etk50pid.exe file is a patch that launches a revised Windows CE Embedded
	Toolkit for Visual C++ 5.0 setup, allowing proper product identification
	(Product ID) numbers to be displayed (to view the Product IDs in Developer
	Studio, on the Help menu, click About).
	
	The Product ID number is necessary to access free support incidents that are
	included with the toolkit. The Windows CE Embedded Toolkit for Visual C++ 5.0
	setup may not have correctly added the product IDs (to view the Product IDs in
	Developer Studio, on the Help menu, click About) so that you can refer to them
	during a support call. These numbers may appear in the form
	80923-xxx-xxxxxxx-55555. All of the x's should have been replaced by digits.
	
	To install the patch, run Etk50pid.exe to extract the patch files into the system
	temporary directory, and automatically start the Setup program. Proceed with the
	setup as usual. When prompted, enter the CD key provided with your product.
	Finally, select any install option and click Exit to complete the update.
	
	This setup will NOT reinstall the product; you will need to reboot your computer.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	Etk50pid.exe
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	
	Additional query words: kbwince200 kboak kbvc500
	
	======================================================================
	Keywords          : kbfile kbpatch kbOAK kbOSWinCE200 
	Technology        : kbAudDeveloper kbWinCEETKSearch kbWinCESearch kbWinCEETKVC500
	Version           : WINDOWS:
	
	=============================================================================
	

{% endraw %}
