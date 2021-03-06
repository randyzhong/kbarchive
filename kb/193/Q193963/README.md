---
layout: page
title: "Q193963: Conversion Errors Result when Return Value is Repositioned"
permalink: /kb/193/Q193963/
---

## Q193963: Conversion Errors Result when Return Value is Repositioned

{% raw %}

	Article: Q193963
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:1.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft COM Transaction Integrator for CICS and IMS, version 1.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A variety of type conversion errors may occur when the return value of a method
	has been repositioned. Specifically, the return value must be a recordset with
	the Occurs Depending On (ODO) attribute specified. By default, the return value
	is defined before other parameters. However, it is possible to reposition the
	return value so that it follows other parameters. One reason for repositioning
	the return value is when it is a recordset with an (ODO) specification. It must
	be repositioned to a location following the ODO parameter.
	
	A variety of COMTI runtime errors may occur at type conversion time; the
	following is an example.
	
	A COMTI runtime error occurs when an output parameter of COBOL PIC 9(n) DISPLAY
	(zoned decimal, numeric) type is presented to COMTI for conversion. For example,
	the automation type is long and the COBOL type is PIC 9(3) DISPLAY. A SNA Server
	trace shows the following data is returned from the mainframe 0xF1F2F3. The data
	is correct for the COBOL type, but COMTI flags the following error.
	
	  Event ID: 102
	  Source: COMTI
	  Type: Error
	  Category: General
	
	  (102) COM Transaction Integrator reported the following exception to a
	  client:
	
	  Component: CUServer.Search.1
	  Method: GetInfo
	
	  Exception description:
	  (1562) Parameter HEADER_LENGTH in method GetInfo contained an invalid zoned
	  decimal value.
	  Check the mainframe server program. If it is correct, verify that the correct
	  COM Transaction Integrator-created component library is deployed.
	
	CAUSE
	=====
	
	COMTI conversion routines always process the return value first, regardless of
	its "position" with respect to other parameters. Therefore, repositioning the
	return value so that it is not first can cause a variety of errors in converting
	other parameters. This occurs because buffer pointers become incorrect during
	the series of conversions.
	
	STATUS
	======
	
	Microsoft has planned to correct this problem in SNA Server version 4.00 U.S.
	Service Pack 2. This supported feature is now available as a hotfix, but has not
	been fully regression tested and should be applied only to systems having a
	specific need for it. Unless you are severely impacted by this problem,
	Microsoft recommends that you wait for the next Service Pack that contains the
	correction. Contact Microsoft Technical Support for more information.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbCOMTISearch kbCOMTI100SP1
	Version           : WINDOWS:1.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
