---
layout: page
title: "Q125440: Modifications to System Files Made by Media Vision Premium/Pro"
permalink: /kb/125/Q125440/
---

## Q125440: Modifications to System Files Made by Media Vision Premium/Pro

{% raw %}

	Article: Q125440
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Media Vision Premium 3-D Sound Card 
	- Media Vision Pro 3-D Sound Card 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article lists the modifications made to the following configuration files
	when you install the Media Vision Premium 3-D or Media Vision Pro 3-D sound
	card:
	
	- CONFIG.SYS
	
	- AUTOEXEC.BAT
	
	- SYSTEM.INI
	
	For additional information about Media Vision products, contact:
	
	- Media Vision's bulletin board service (BBS): (510) 770-0968
	
	- Media Vision's Word-Wide Web site on the Internet:
	
	  http://www.mediavis.com
	
	- Media Vision's CompuServe forum: GO MEDIAVISON
	
	- Media Vision product support, phone: (503) 882-1177
	
	CONFIG.SYS
	----------
	
	     DEVICE=C:\MEDVSN\PA3D.SYS A220 D1 I7 H7 M320 Q2
	
	AUTOEXEC.BAT
	------------
	
	     SET  BLASTER=A220  I7  D1  H7  T4
	
	SYSTEM.INI
	----------
	
	     [BOOT]
	     SOUND.DRV=MMSOUND.DRV
	     DRIVERS=MMSYSTEM.DLL MSMIXMGR.DLL MMMIXER.DLL
	
	     [386ENH]
	     DEVICE=VPA3DD.386
	     DMABUFFERSIZE=064
	
	     [MCI]
	     CDAUDIO=MCICDA.DRV
	
	     [DRIVERS]
	     WAVE=PA3DWAVE.DRV
	     MIXER=PA3DMXD.DRV
	     MIDI=MVIFM.DRV
	     MIDI1=PA3D401.DRV
	
	     [PA3DWAVE.DRV]
	     PORT=220
	     INT=7
	     DMACHANNEL=1
	     DMACHANNEL2=7
	
	     [PA3D401.DRV]
	     INT=2
	     PORT=320
	     BOARD=0
	
	Entries Appearing in the Control Panel
	--------------------------------------
	
	  Media Vision 401 Midi Driver
	  Media Vision FM Synth Driver
	  Media Vision Mixer Driver
	  Media Vision Wave Driver
	  MIDI Mapper
	  Timer
	  [MCI]CD Audio
	  [MCI]MIDI Sequencer
	  [MCI]Sound
	
	MORE INFORMATION
	================
	
	Possible CONFIG.SYS file PA3D.SYS parameters may be:
	
	  A#      Base addresses for the sound card: 210, 220, 230, 240, 250,
	          260. DO NOT use 230 unless the sound card's SCSI host
	          address is removed. Default is A220.
	
	  D#      Sound Blaster 8-bit DMA channels 1 and 3. Default is D1.
	
	  I#      IRQ assignment for the board: 2,3,5,7,10, and 15. Default
	          is I7.
	
	  H#      16-bit DMA channel: 5 and 7. Default is H7.
	          NOTE: on the Media Vision Premium 3-D, the 16-bit DMA channel
	can also be set to 1
	
	  M#      MPU-401 emulation base address: 300, 310, 320 and 330.
	          Default is M320.
	
	  Q#      MPU-401 emulation IRQ: 2, 3, 5, and 7. Default is Q2.
	
	Optional Parameters
	
	  V       Displays all hardware settings during driver load.
	
	  N       Don't print sign-on banner.
	
	The third-party products discussed here are manufactured by vendors independent
	of Microsoft; we make no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	Additional query words: kbhowto multi media multimedia multi-media kbdisplay kbsound kbhw mmtitles audio 3d
	
	======================================================================
	Keywords          :  
	Technology        : kb3rdpartySearch kbZNotKeyword3
	Version           : :
	
	=============================================================================
	

{% endraw %}
