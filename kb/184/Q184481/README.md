---
layout: page
title: "Q184481: XCON: MTACheck Causes Access Violation"
permalink: /kb/184/Q184481/
---

## Q184481: XCON: MTACheck Causes Access Violation

{% raw %}

	Article: Q184481
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you run MTACHECK, it may fail with a Dr. Watson exception error. When you
	view the DRWTSN32.log, you may see the following exception error:
	
	  Application exception occurred:
	       App: MTACHECK.EXE (pid=411)
	       When: 1/21/1997 @ 3:37:20.133
	       Exception number: c0000005 (access violation)
	
	  (00400000 - 00540000) ..\..\BIN\MTACHECK.EXE
	  (77f80000 - 77fce000) dll\ntdll.DBG
	  (77f20000 - 77f74000) dll\kernel32.DBG
	  (77e20000 - 77e4d000) dll\advapi32.DBG
	  (77e60000 - 77e9c000) dll\rpcrt4.DBG
	  (6d570000 - 6d577000) exchmem.DBG
	  (10200000 - 10251000)
	  (77e50000 - 77e55000) dll\rpcltc1.DBG
	
	  State Dump for Thread Id 0x19a
	
	  eax=00000000 ebx=00000020 ecx=00000006 edx=006cfeec esi=004ec7c2
	  edi=00144800
	  eip=00425e55 esp=0012e5e0 ebp=0012e5e4 iopl=0     nv up ei ng nz na   po
	  nc
	  cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000
	  efl=00000286
	
	  function: odpldbin
	       00425e2d ff86b0000000     inc     dword ptr [esi+0xb0]
	  ds:004ec872=000e084f
	       00425e33 50               push    eax
	       00425e34 e8a77c0200       call    memset (0044dae0)
	       00425e39 66b90800         mov     cx,0x8
	       00425e3d 83c40c           add     esp,0xc
	       00425e40 66c786d60000000000 mov   word ptr [esi+0xd6],0x0
	  ds:004ec898=0000
	       00425e49 c6460800         mov     byte ptr [esi+0x8],0x0
	  ds:00a5b0e4=00
	       00425e4d 833e00           cmp     dword ptr [esi],0x0
	  ds:004ec7c2=ffffffff
	       00425e50 740c             jz      odpldbin+0x6e (00425e5e)
	       00425e52 8b4609           mov     eax,[esi+0x9]
	  ds:00a5b0e4=00000000
	  FAULT ->00425e55 8b5008           mov     edx,[eax+0x8]
	  ds:0056e922=00000000
	       00425e58 8a4208           mov     al,[edx+0x8]
	  ds:00c3e80e=??
	       00425e5b 884608           mov     [esi+0x8],al
	  ds:00a5b0e4=00
	       00425e5e 83c611           add     esi,0x11
	       00425e61 6649             dec     cx
	       00425e63 75e4             jnz     odpldbin+0x59 (00425e49)
	       00425e65 5e               pop     esi
	       00425e66 5d               pop     ebp
	       00425e67 c20400           ret     0x4
	       00425e6a 8d9b00000000     lea     ebx,[ebx]
	  ds:00000020=????????
	
	  *----> Stack Back Trace <----*
	
	  FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name
	  0012e5e4 00426d4c 0012f1d8 00144800 77f333a6 00000040 MTACHECK!odpldbin
	  0012f3bc 0042e81e 00000001 00509ca0 005196a0 0012fc28 MTACHECK!odpgrcvr
	  0012fc2c 0042da82 00144800 77f333a6 7ffdf000 00000000 MTACHECK!odpgimai
	  0012ff00 00442d42 00144800 77f333a6 7ffdf000 00000000 MTACHECK!odpgmtin
	  0012ff84 004447e9 00144800 77f333a6 7ffdf000 0012ff8c MTACHECK!sbpwinit
	  0012ffb0 0044d817 00000002 002f0d00 002f0d20 00144800 MTACHECK!main
	  0012fff0 00000000 7ffdf000 00000000 00000000 77fb8bf0
	  MTACHECK!mainCRTStartup
	  00000000 00000000 00000000 00000000 00000000 00000000
	  MTACHECK!<nosymbols>
	
	CAUSE
	=====
	
	MTACheck is trying to update the flags on an attachment while the attachments
	are bound to a queue that does not exist.
	
	WORKAROUND
	==========
	
	Run MTACheck for a second time and the queue will be re-created.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Exchange Server version 4.0. We
	are researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	
	
	
	Additional query words: XCON MTA MTACHECK QUEUE GPF
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : WINDOWS:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
