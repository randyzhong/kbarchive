---
layout: page
title: "Q178344: XADM: IS Uses 100% of CPU and Generates Access Violation"
permalink: /kb/178/Q178344/
---

## Q178344: XADM: IS Uses 100% of CPU and Generates Access Violation

{% raw %}

	Article: Q178344
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 21-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	An IMAIL conversion thread is caught in a loop due to an incorrectly formatted
	MIME message. As a result, the Microsoft Exchange Server Information Store CPU
	utilization jumps to 100 percent and the Information Store will eventually
	generate an access violation.
	
	CAUSE
	=====
	
	The Thread handling this message is caught between commit opperations for two
	converters.
	
	The Microsoft Exchange Information Store issues a commit operation, and the HR
	returned is 80040c11. According to the comments before IsIMAILRewindError, these
	errors indicated that the message should be reconverted. This error is
	IMAIL_E_REWIND_STREAM_822, which is supposed to cause a rewind, then process as
	822. The Information Store passes this into the Clean up function, which should
	set the rewriter to Convert to 822. It does. The Information Store continually
	sets the rewind error to be rewind and convert as 822, but it never succeeds or
	changes.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.0.
	
	This problem has been corrected in the latest U.S. Service Pack for Microsoft
	Exchange Server version 5.0. For information on obtaining the Service Pack,
	query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	If you are experiencing this problem, the call stack shown in the Dr.Watson dump
	(and log) will look like the one below (with thousands of calls to
	EcCommitStream and EcCommitStreamOp).
	
	  FramePtr  RetAddr   Param1   Param2   Param3   Function Name
	  062ef89c  004700d2  00000023 00000004 00000001
	  STORE!EcCommitStreamOp+0x88
	  062ef8ac  004044c6  00000001 00000023 062ef948 STORE!EcCommitStream+0x46
	  062ef90c  00403928  062ef928 00005a00 062ef92c STORE!EcRpc+0xb6a
	  062ef928  77e11841  00171330 00f8db6c 00176ec0 STORE!EcDoRpc+0x3e
	  062ef948  77e52265  004038ea 062efb3c 00000004 RPCRT4!Invoke+0x28
	  062ef964  77e52236  004038ea 062efb3c 00000004
	  RPCRT4!NdrCallServerManager+0x15
	  062efc28  77e51f9e  00000000 00000000 062efe08 0x77e52236
	  062efc40  77e1134f  062efe08 062efe08 00163380 RPCRT4!NdrServerCall+0x19
	  062efc7c  77e11122  00404af4 062efe08 062efdc4
	  RPCRT4!DispatchToStubInC+0x34
	  062efcd0  77e112fb  062efe08 00000000 062efdc4
	  RPCRT4!?DispatchToStubWorker@RPC_INTERFACE@@AAEJPAU_RPC_
	  MESSAGE@@IPAJ@Z+0xb0
	  062efcf0  77e119cf  062efe08 00000000 062efdc4
	  RPCRT4!?DispatchToStub@RPC_INTERFACE@@QAEJPAU_RPC_MESSAGE@@IPAJ@Z+0x41
	  062efdc8  77e12b98  00144360 062efe68 062efe08
	  RPCRT4!?DealWithRequestMessage@WMSG_SASSOCIATION@@QAEXPAT_WMSG_
	  MESSAGE@@0PAU_RPC_MESSAGE@@PAPAVWMSG_SBINDING@@IHH@Z+0x182
	  062efe40  77e15fff  00144360 062efe68 00000000
	  RPCRT4!?DealWithLRPCRequest@WMSG_ADDRESS@@AAEPAT_WMSG_
	  MESSAGE@@PAT2@0HPAVWMSG_ASSOCIATION@@@Z+0xab
	  062eff90  77e162f0  77e163e5 001545f0 062effec
	  RPCRT4!?ReceiveLotsaCalls@WMSG_ADDRESS@@AAEXXZ+0x38
	
	
	Additional query words: store.exe
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : WinNT:5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
