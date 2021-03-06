---
layout: page
title: "Q157636: HOWTO: Set Up Source Code Control with Visual SourceSafe"
permalink: /kb/157/Q157636/
---

## Q157636: HOWTO: Set Up Source Code Control with Visual SourceSafe

{% raw %}

	Article: Q157636
	Product(s): Microsoft SourceSafe
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbinterop kbSSafe400 kbSSafe500 kbSSafe600 kbvfp500
	Last Modified: 19-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	- Microsoft Visual FoxPro for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to setup a Visual FoxPro for Windows project under
	SourceCode Control so that it can be accessed by multiple users.
	
	MORE INFORMATION
	================
	
	1. Run Visual SourceSafe Administrator. On the Tools menu, click Options. In the
	  General tab of the "SourceSafe Options" dialog box, check the "Allow Multiple
	  Checkouts" option and clear the "Use network name for automatic user log in"
	  option if you are opening two sessions of SourceSafe on the same computer.
	
	2. Add two new users in Visual SourceSafe: SCTST1 and SCTST2. Close the Visual
	  SourceSafe Administrator.
	
	3. Run the Visual SourceSafe Client and login as SCTST1. On the File menu, click
	  Set Working Directory. Enter "..\SCTST1wd" as the working directory and click
	  the "Create Dir" button to create the directory if it does not already exist.
	  Close Visual SourceSafe.
	
	4. Run Visual SourceSafe Client. Repeat step 3 above, but this time login in as
	  SCTST2, and set the working directory to "..\SCTST2wd". Close Visual
	  SourceSafe.
	
	5. Run Visual FoxPro for Windows. On the Tools menu, click Options.
	
	6. Select the Projects tab and set "Active Source Control Provider" to
	  "Microsoft Visual SourceSafe."
	
	7. Click on the "Set as Default" button, and close the Options dialog box.
	
	8. Open the Tastrade project in "..\Vfp\Samples\Tastrade\."
	
	9. On the Project menu, click "Add Project to Source Control." When prompted,
	  log on to Visual SourceSafe as SCTST1.
	
	NOTE: After being added to Source Control, the project and its components remain
	in the same directory, and a project meta file (.pjm) is added to that
	directory. In the case of this example, the name of the .pjm file is
	Tastrade.pjm. For more information on the project meta file, please refer to the
	"Managing Visual FoxPro Projects Under Source Control" topic in the "Developing
	in Teams" chapter of the Visual FoxPro Developer's Guide.
	
	1. After the project is added to source code control, start a second instance of
	  Visual FoxPro for Windows on the same or different machine. If Visual
	  SourceSafe is not set up as the active source control provider, follow steps
	  5, 6, and 7 above to do so.
	
	2. On the File menu, click "Join Source Control Project." When prompted log on
	  to Visual SourceSafe as SCTST2.
	
	3. In the "Open SourceSafe Project" dialog box, select the Tastrade project.
	  Click the Browse button from the "Open SourceSafe Project" dialog box. The
	  "Browse Directory" dialog box appears. Locate the working directory. If the
	  working directory does not exist, enter the directory name, "..\SCTST2wd" for
	  example, and click the "Create Dir" button. Close the "Browse Directory"
	  dialog box.
	
	4. Select "Yes All" in all the dialog boxes that come up.
	
	NOTE: The "Join Source Control Project" process copies the project and its
	components, which were placed under Source Control, to the working directory
	that is specified for the user(SCTST2) in Visual SourceSafe. This process also
	checks out a copy of the .pjm file (Tastrade.pjm) to the working directory.
	
	1. Close the project in both sessions of Visual FoxPro for Windows.
	
	2. In the First Session of Visual FoxPro for Windows, open the Tastrade Project
	  in the "..\Vfp\Samples\Tastrade\" directory.
	
	3. In the second session of Visual FoxPro for Windows, open the Tastrade project
	  in "...\SCTST2wd."
	
	4. The user should be able to Check Out, Modify, and Check In files from both
	  sessions of Visual FoxPro.
	
	5. To update the Projects in each session, use the "Update Project List" option
	  in the "Source Control" menu under the Project menu.
	
	The user (SCTST1) who Added the project to source control may want to work on the
	project in a directory other than "..\Vfp\Samples\Tastrade\." To allow this,
	repeat steps 11-12 with the following exceptions:
	
	- In step 11, log on to Visual SourceSafe as SCTST1.
	
	- In step 12, instead of selecting "..\SCTST2wd" as the working directory,
	  select "..\SCTST1wd".
	
	REFERENCES
	==========
	
	Visual FoxPro Online Developer's Guide, Developing in Teams chapter, "Managing
	Visual FoxPro Projects Under Source Control"
	
	Additional query words:
	
	======================================================================
	Keywords          : kbinterop kbSSafe400 kbSSafe500 kbSSafe600 kbvfp500 
	Technology        : kbVFPsearch kbSSafeSearch kbAudDeveloper kbVFP500 kbSSafe600 kbSSafe500
	Version           : :5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
