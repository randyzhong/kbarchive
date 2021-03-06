---
layout: page
title: "Q185900: Configuring SNA Server and Exchange for SNADS Connectivity"
permalink: /kb/185/Q185900/
---

## Q185900: Configuring SNA Server and Exchange for SNADS Connectivity

{% raw %}

	Article: Q185900
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,3.0,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 3.0, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When configuring SNA Server to provide the underlying connectivity for the
	Microsoft Exchange SNADS (System Network Architecture Distribution Services)
	connector (formerly known as Linkage), certain parameters must match or the
	application will fail to connect.
	
	1. Add a connection in the SNA Manager to the AS/400, or to the host system
	  corresponding to a particular PU, (physical unit) on the host. See the
	  Microsoft SNA Server Administration Guide and TechNet for relevant
	  information to the connection configuration.
	
	2. Add a local Advanced Program-to-Program Communications Logical Unit (APPC
	  LU), that corresponds to the host-defined PU parameters. The local LU will
	  correspond to the Locaddr=0 in the PU definition (if implementing Independent
	  LU6.2) or LU #2 or higher (if doing Dependent LU6.2). If implementing
	  dependent LU 6.2 Local LUs, you need to define two LUs. One will be used to
	  send to the host. The other will receive from the host. For AS/400
	  connections, independent LU 6.2 will be used, and the local LU does not need
	  any specific LU name.
	
	NOTE: With Independent LU 6.2, only a single Local LU is necessary on the SNA
	Server to provide bi-directional send and receive capability for the SNADS
	connector. If using Dependent LU6.2 for SNADS, you must define two local LUs:
	one to send to the host and one to receive from the host.
	
	1. Define a Remote APPC LU that corresponds either to the AS/400's local
	  control-point name (you find the control-point name by performing a DSPNETA
	  at a 5250 command prompt), or to the host-defined CICS region parameters.
	  This should be the APPLID value in the CICS region. The value is often
	  DISOSS, but it may differ if the host-side configuration is different.
	
	2. Define a mode name to be used for the LU6.2 sessions. The mode name must
	  correspond to the Modename defined in the CICS region on the host side.
	
	NOTE: Sample parameters for configuring an SNA Server can be found in the SNA
	Server Administration Guide|How Do I configure VTAM For APPC Access.
	
	1. Save the configuration when the connection, the Local LU, and the Remote LU,
	  have been set up in the SNA Manager. You can test this configuration by going
	  to the Tools menu in the SNA Manager and selecting the APPC Session Viewer.
	  When the APPC Session Viewer comes up, click the LU-LU Test button. The LU-LU
	  Test screen will appear. Type in the Local LU, Remote LU, and the Mode, that
	  will be used by the SNADS connector in the Corresponding boxes. Then select
	  Start Test to initiate CNOS (Change Number Of Sessions) negotiation. If the
	  negotiation is successful, the node name (SNA Server) and the negotiation
	  information will appear in the window, showing how many sessions were
	  negotiated and the sessions in use.
	
	If the APPC connectivity is confirmed by following step 5, then any problem
	encountered is likely to be in configuration of the Microsoft Exchange software.
	Many times the incorrect configuration is due to an incorrect parameter
	specified that does not match host or AS/400 settings. When setting up the SNADS
	connector, the following parameters will need to be filled in for correct
	application execution. Below is a list of the configuration options in the
	Connector for SNADS Properties sheet for Exchange:
	
	Local RGN
	---------
	
	This is the host-defined Routing Group Name. This parameter is only necessary if
	specified on the host side. It can otherwise be left blank. This is a parameter
	supplied by the host or by the AS/400 Administrator.
	
	Local REN
	---------
	
	This is the host-defined parameter representing the connector for the SNADS DSU
	(Distribution Service Unit) Routing Element Name. For DISSOS, this must match
	the connector entry in the DISOSS Routing Table. For AS/400, it must match the
	connector entry in the AS/400 Routing Table. This is a parameter supplied by the
	host or by the AS/400 Administrator.
	
	Partner RGN
	-----------
	
	This is the SNADS Routing Group Name. This is not necessary unless you are using
	RGNs. This is a parameter supplied by the host or by the AS/400 Administrator.
	
	Partner REN
	-----------
	
	This is the SNADS partner's Routing Element Name. This is a parameter supplied by
	the host or by the AS/400 Administrator.
	
	Local LU Alias
	--------------
	
	This parameter should match the Local LU configured on the Microsoft SNA Server
	in step two above.
	
	Partner LU Alias
	----------------
	
	[ASCII 160][ASCII 160][ASCII 160] This parameter should match the Remote LU
	configured on the Microsoft SNA Server in step three above.
	
	Receive Local LU
	----------------
	
	This is the Local LU alias used to receive mail from the host system. Specify
	this value only if the configuration is set up for dual dependent LU 6.2
	sessions. Leave this field blank when you are connecting through a single,
	independent LU 6.2 Local LU.
	
	Node Name
	---------
	
	The Node Name is used by the connection to locate the appropriate SNA Server in a
	client/server environment. If you want the service provided by the local SNA
	Server, remove the NodeName statement or assign blanks. This instructs the
	connector to locate the local ActiveComputerName from the Windows NT registry.
	If the computer name of a remote SNA Server is specified, the connector will
	broadcast SNA System Management Verbs to a remote SNA Server. This name must
	match the AS/400 Remote Location Name and the SNA Server Properties Control
	Point name.
	
	Mode Name
	---------
	
	The LU6.2 mode name used for the TP. This must match the SNA Server mode
	definition and the AS/400 MODD parameter. If the connector is connected to a
	SNADS partner using an independent LU6.2 Local LU, it is recommended that the
	#BATCH mode be used. This is the most common mode for implementation.
	
	Maximum Number of Connection Attempts
	-------------------------------------
	
	The number of times the Exchange SNADS connector attempts to connect to the SNADS
	partner. The default, zero, indicates infinite retry. This has nothing to do
	with the timeout and inactivity timers (t1, t2, and ti) in the connection
	properties of a SNA Server 802.2 connection.
	
	Delay Between Attempts
	----------------------
	
	This is the number of seconds the Exchange SNADS waits between connection
	attempts to the SNADS partner.
	
	Maximum Number of Hops
	----------------------
	
	The maximum number of "store-and-forward" locations that a message is allowed
	before it is rejected. The default setting for this is 60.
	
	Maximum Number of Days to Keep Proxy Address
	--------------------------------------------
	
	The number of consecutive days that an unused proxy address can stay in the
	Microsoft Exchange Server personal address book. The default is 180 days.
	
	MORE INFORMATION
	================
	
	The information below is from appendix A of the Microsoft Exchange Server v. 5.5
	Help File:
	
	Host Configuration Examples and Alternatives
	--------------------------------------------
	
	CICS TCT Definitions In the following example, two TCT definitions are used to
	define the connector.
	
	NOTE: If you define the connector to CICS using TCT definitions, see the
	Microsoft Exchange Server Help File, v. 5.5: Chapter 2, "Preparing the DISOSS
	Host Environment," for parameter descriptions.
	
	     DFHTCT   TYPE=SYSTEM,
	
	           ACCMETH=VTAM,
	           TRMTYPE=LUTYPE62,
	           FEATURE=SINGLE,
	           TRMSTAT=TRANSCEIVE,
	           NETNAME=LULAN1,
	           MODENAME=LANMODE,
	           SYSIDNT=LAN1,
	           RUSIZE=256,
	           CONNECT=AUTO
	
	     DFHTCT   TYPE=SYSTEM,
	
	           ACCMETH=VTAM,
	           TRMTYPE=LUTYPE62,
	           FEATURE=SINGLE,
	           TRMSTAT=TRANSCEIVE,
	           NETNAME=LULAN2,
	           MODENAME=LANMODE,
	           SYSIDNT=LAN2,
	           RUSIZE=256,
	           CONNECT=AUTO
	
	CICS RDO Definitions
	--------------------
	
	If you plan to define the connector to CICS through RDO using CONNECTION and
	SESSION definitions, see the Microsoft Exchange Server Help File, v. 5.5:
	Chapter 2, "Preparing the DISOSS Host Environment," for parameter descriptions.
	
	In the following example, the connector is defined using a CONNECTION definition.
	LAN1 is used for routing mail traffic from the host to the LAN; LAN2 is used for
	routing mail traffic from the LAN to the host.
	
	     DEFINE   CONNECTION (LAN1) GROUP (LNKLANS)
	           
	           NETNAME (LULAN1) ACCESSMETHOD (VTAM)
	           PROTOCOL (APPC) SINGLESESS (YES)
	           AUTOCONNECT (YES)
	     
	  DEFINE   CONNECTION (LAN2) GROUP (LNKLANS)
	
	           NETNAME (LULAN2) ACCESSMETHOD (VTAM)
	           PROTOCOL (APPC) SINGLESESS (YES)
	           AUTOCONNECT (YES)
	
	In the following example, the connector is defined using a SESSION definition.
	LAN1S is used for routing mail traffic from the host to the LAN and LAN2S is
	used for routing mail traffic from the LAN to the host.
	
	     DEFINE   SESSIONS (LAN1S) GROUP (LNKLANS)
	
	           CONNECTION (LAN1)
	           MODENAME (LANMODE) PROTOCOL (APPC)
	            AUTOCONNECT (YES) SENDSIZE (256)
	           RECEIVESIZE (256) MAXIMUM (1,0)
	
	     DEFINE   SESSIONS (LAN2S) GROUP (LNKLANS)
	
	           CONNECTION (LAN2)
	           MODENAME (LANMODE) PROTOCOL (APPC)
	            AUTOCONNECT (YES) SENDSIZE (256)
	           RECEIVESIZE (256) MAXIMUM (1,0)
	
	DISOSS ROUTING Definition
	-------------------------
	
	In the following example, the QUEUE references a SYSIDNT or CONNECTION of LAN1.
	The first DHFTCT or RDO definition is always used by the DISOSS system to send
	mail.
	
	     ADD   RGN=,
	
	        REN=LANREN,
	        SSL=*
	        TRANSID=DSVE,
	        QUEUE=LAN1
	
	DISOSS HUP Definition
	---------------------
	
	The following is an example of a DISOSS Host User Profile for any user in the
	workgroup called LANDGN.
	
	     ADD   USERTYPE=REMOTE,
	
	        DDN=LANDGN,
	        SA=*
	        RGN=,
	        REN=LANREN
	
	Sample NCP/VTAM Definitions
	---------------------------
	
	The following is an example of a link definition.
	
	     LANNET   VBUILD TYPE=SWNET,
	
	           MAXGRP=1,
	           MAXNO=64
	
	Token-Ring Attachment Through an IBM 37x5 TIC
	---------------------------------------------
	
	This example illustrates the configuration for a Token-Ring connection to an IBM
	37x5 Token-Ring interface controller (TIC).
	
	  LNK02   LINE   ADDRESS=(131,FULL),
	
	              LOCADDR=400037450001,
	              PORTADD=01,
	              ANS=CONT,
	              CLOCKING=EXT,
	              DUPLEX=FULL,
	              MAXPU=1,
	              RETRIES=(7,1,7),
	              SERVLIM=32,
	              NRZI=NO,
	              ISTATUS=ACTIVE
	              SERVICE MAXLIST=1
	
	     LNK02A   PU   ADDR=C1,
	
	              PUTYPE=2,
	              IBBLK=05D, IDNUM=000C1,
	              PASSLIM=7,
	              MAXOUT=7,
	              MAXLU=2,
	              DATMODE=HALF,
	              MAXDATA=1033,
	              PACING=7, VPACING=7,
	              SSCPFM=FSS,
	              ISTATUS=ACTIVE,
	              IRETRY=NO
	
	     LNKPATH   PATH   DIALNO=0104400000000001
	
	     LNKGWLU1    LU   LOCADDR=01,
	
	              USSTAB=,
	              LOGAPPL=,
	              SSCPFM=FSS
	
	     LNKGWLU2    LU   LOCADDR=02,
	
	              USSTAB=,
	              LOGAPPL=,
	              SSCPFM=FSS
	
	Token Ring Attachment Through a Local 3174TokenRing Controller
	--------------------------------------------------------------
	
	In the following example, the connection is through Token Ring to a local 3174
	channel that is attached to the host VTAM. The gateway control unit address is
	D71, which represents the Token Ring address 400000170001.
	
	     LANNET   VBUILD       TYPE=LOCAL
	
	     LNK02A   PU   CUADDR=D71,
	
	              PUTYPE=2,
	              PASSLIM=7,
	              MAXOUT=7,
	              MAXLU=2,
	              DATMODE=HALF,
	              MAXDATA=1033,
	              PACING=7, VPACING=7,
	              SSCPFM=FSS,
	              ISTATUS=ACTIVE,
	              IRETRY=NO
	
	  LNKGWLU1   LU   LOCADDR=01,
	
	           USSTAB=,
	           LOGAPPL=,
	           SSCPFM=FSS
	
	  LNKGWLU2   LU   LOCADDR=02,
	
	           USSTAB=,
	           LOGAPPL=,
	           SSCPFM=FSS
	
	The Token Ring network address assignment on a local 3174 controller (for
	example, 3174-01L) should include a mapping similar to the following examples.
	
	S@   Ring@   SAP@   T   F   W
	
	D70   400000170000   04   0   0   2
	D71   400000170001   04   0   0   2
	
	In this scenario, a locally administered address X'400000170000' is assigned to
	the 3174 IBM Token Ring network adapter, and a locally administered address
	X'400000170001' is assigned to the connector.
	
	Token Ring Attachment Through a Remote 3174TokenRing Controller
	---------------------------------------------------------------
	
	In the following example, the connection is through Token Ring to a 3174 that is
	remotely attached on an SDLC line to the host VTAM. The gateway control unit
	address is C2, which represents the Token Ring address 4000 0017 0001.
	
	     LNK02A   PU   ADDR=C2
	
	           PUTYPE=2,
	           PASSLIM=7,
	           MAXOUT=7,
	           MAXLU=1,
	           DATMODE=HALF,
	           MAXDATA=1033,
	           PACING=7, VPACING=7,
	           SSCPFM=USSSCS,
	           ISTATUS=ACTIVE,
	           IRETRY=NO
	
	     LNKGWLU1    LU   LOCADDR=01,
	
	              USSTAB=,
	              LOGAPPL=,
	              SSCPFM=FSS
	
	     LNKGWLU2    LU   LOCADDR=02,
	
	              USSTAB=,
	              LOGAPPL=,
	              SSCPFM=FSS
	
	The Token Ring network address assignment on a 3174 controller should include a
	mapping similar to the following examples.
	
	S@   Ring@   SAP@   T   F   W
	
	C1   400000170000   04   0   0   2
	C2   400000170001   04   0   0   2
	
	In this scenario, a locally administered address X'400000170000' is assigned to
	the 3174 IBM Token Ring network adapter, and a locally administered address
	X'400000170001' is assigned to the connector.
	
	Non-switched SDLC Link
	----------------------
	
	In the following example, the connection is through a dial-up leased line.
	
	  Microsoft   GROUP   LNCTL=SDLC
	
	     LNK01   LINE   ADDRESS=(131,FULL),
	
	                 ANS=CONT,
	                 CLOCKING=EXT,
	                 DUPLEX=FULL,
	                 MAXPU=1,
	                 RETRIES=(7,1,7),
	                 SERVLIM=32,
	                 NRZI=NO,
	                 ISTATUS=ACTIVE,
	                 SPEED=9600
	                 SERVICE MAXLIST=1
	
	     LNK01A   PU      PUTYPE=2,
	
	                 ADDR=C1,
	                 PASSLIM=7,
	                 MAXOUT=7,
	                 MAXLU=2,
	                 DATMODE=HALF,
	                 MAXDATA=265,
	                 PACING=7, VPACING=7,
	                 SSCPFM=FSS,
	                 ISTATUS=ACTIVE
	
	     LNKGWLU1    LU      LOCADDR=01,
	
	                 USSTAB=,
	                 LOGAPPL=,
	                 SSCPFM=FSS
	
	     LNKGWLU2 LU      LOCADDR=02,
	
	                 USSTAB=,
	                 LOGAPPL=,
	                 SSCPFM=FSS
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ211 kbSNAServ400
	Version           : WINDOWS:2.11,3.0,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
