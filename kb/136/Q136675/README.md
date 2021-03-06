---
layout: page
title: "Q136675: Changing Sound Blaster 16 HDMA Settings in Windows 95/98"
permalink: /kb/136/Q136675/
---

## Q136675: Changing Sound Blaster 16 HDMA Settings in Windows 95/98

{% raw %}

	Article: Q136675
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1.0,1.0a,2.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbenv kbsound kbtlc kbimukbfaq
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Ancient Lands for Windows, version 1.0 
	- Microsoft Art Gallery for Windows, version 1.0 
	- Microsoft Bookshelf '95 for Windows 95 
	- Microsoft Bookshelf 1996-97 for Windows 
	- Microsoft Bookshelf for Windows, 1995 Intro Edition 
	- Microsoft Cinemania for Windows, 1992, 1993, 1994, 1995, 1996, 1997 editions 
	- Microsoft Complete Baseball for Windows, 1994 edition (see below) 
	- Microsoft Complete Baseball Guide for Windows, 1995 edition 
	- Microsoft Complete Gardening for Windows, version 1.0 
	- Microsoft Complete NBA Basketball for Windows, 1994-1995, 1995-1996 editions 
	- Microsoft Creative Writer for Windows, version 1.0 
	- Microsoft Dangerous Creatures for Windows, version 1.0 
	- Microsoft Dinosaurs for Windows, version 1.0 
	- Microsoft Encarta Intro Edition, 1995 edition 
	- Microsoft Encarta 96 Encyclopedia for Windows 
	- Microsoft Encarta 97 Encyclopedia for Windows 
	- Microsoft Encarta Encyclopedia 97 Deluxe for Windows 
	- Microsoft Encarta 96 World Atlas for Windows 
	- Microsoft Explorapedia series: World of Nature for Windows, version 1.0 
	- Microsoft Fine Artist for Windows, version 1.0 
	- Microsoft How the Leopard Got His Spots, version 1.0 
	- Microsoft Isaac Asimov's The Ultimate Robot for Windows, version 1.0 
	- Microsoft Music Central for Windows, 1996, 1997 edition 
	- Microsoft Musical Instruments for Windows, version 1.0 
	- Microsoft Multimedia Mozart for Windows, version 1.0 
	- Microsoft Multimedia Schubert for Windows, version 1.0 
	- Microsoft Multimedia Strauss for Windows, version 1.0 
	- Microsoft Multimedia Stravinsky for Windows, version 1.0 
	- Microsoft Reader's Digest Complete Do-It-Yourself Guide for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Human Body for Windows, version 1.0 
	- Microsoft SoundBits (all collections), version 1.0 
	- Microsoft Wine Guide for Windows, versions 1.0, 1.0a, 2.0 
	- Microsoft World of Flight for Windows, version 1.0 
	- the operating system: Microsoft Windows 95 
	- the operating system: Microsoft Windows 98 
	- Microsoft Explorapedia series: World of People for Windows, version 1.0 
	- Microsoft Encarta 97 World Atlas for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may be unable to play compressed audio clips if you are using a Sound
	Blaster 16, Sound Blaster 16 ASP or a Sound Blaster AWE 32 sound card. For
	example, you may not be able to play any sounds in Encarta, but the video clips
	may play properly.
	
	You may experience the following symptoms:
	
	- Stuttering sounds
	- Static
	- No sound
	- Computer stops responding (hangs)
	- System abruptly exits Windows
	
	
	CAUSE
	=====
	
	The Sound Blaster 16, 16 ASP, and AWE 32 sound cards use two DMA (Direct Memory
	Access) channels: one channel for 8-bit memory access and one for 16-bit memory
	access. Some computers, however, cannot use 16-bit DMA when using these sound
	cards.
	
	According to the Sound Blaster 16 "Getting Started" manual:
	
	  "Your system's mother board cannot handle 16-bit DMA at full speed. On some
	  machines, the DMA controller on the motherboard does not function properly
	  during 16-bit DMA transfer. 16-bit DMA transfer on such systems might corrupt
	  the data in the main memory and cause the system to hang or encounter a
	  memory parity error."
	
	  "To resolve this problem, select the "use 8-bit DMA" option for the 16-bit DMA
	  channel... when this option is selected, 16-bit PCM data will be transferred
	  through the 8-bit DMA channel."
	
	For more information about Sound Blaster cards and about this problem, please
	contact Creative Labs, the maker of Sound Blaster products, at the following
	telephone numbers:
	
	  Creative Labs Technical Support : (405) 742-6655
	  Frequently Asked Questions (FAQ): (405) 742-6622
	
	RESOLUTION
	==========
	
	To resolve this problem in Windows 95/98, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. On the Device Manager tab, double-click Sound, Video and Game Controllers.
	
	4. Double-click your sound card.
	
	5. On the Resources tab, click the Use Automatic Settings check box to clear it.
	
	6. In the Setting Based On box, click Basic Configuration 7. If you are using
	  the Sound Blaster 16 Plug and Play driver, click Basic Configuration 0004 to
	  use 8-bit DMA only.
	
	7. Click OK, and then click Yes. If you are prompted to restart the computer,
	  click Yes.
	
	If the problem persists, a Basic Configuration of 1 or 5 may also work. Make sure
	when changing the configuration that you check the Conflicting Device List at
	the bottom of the resource tab to check if the selected configuration causes a
	conflict.
	
	If a Basic Configuration does not use a 16-bit DMA resource (DMA channels 5, 6,
	or 7), but does cause a conflict, select a Basic Configuration that does not use
	16-bit DMA and then manually change the conflicting resource.
	
	To change the conflicting resource, follow these steps:
	
	1. Identify the conflict in the Conflicting Device List.
	
	2. Click the conflicting resource in the resource list, and then Change Setting.
	
	3. Click a non-conflicting value for the conflicting resource, and then click
	  OK.
	
	4. Click OK, and then click Yes. If you are prompted to restart the computer,
	  click Yes.
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q106549 Compressed Audio Doesn't Play on Sound Blaster Card
	
	  Q124869 Software Reconfiguration of SoundBlaster 16 Hardware Settings
	
	
	Additional query words: kbmm multi multi-media media mmtitles soundblaster sb16 sb16asp sbawe32 sb distorted fuzzy silent crash freeze lock
	
	======================================================================
	Keywords          : kb3rdparty kbenv kbsound kbtlc kbimu kbfaq
	Technology        : kbOSWin98 kbOSWin95 kbOSWinSearch kbHomeProdSearch _IKkbbogus kbHomeMMsearch kbEncartaSearch kbGamesSearch kbZNotKeyword kbZNotKeyword2 kbKidsSearch kbBookshelfSearch kbSoundBitsSearch kbBaseballSearch kbEncartaEncycSearch kbZNotKeyword3 kbCineManiaSearch kbAncientLands kbCompleteBaseballSearch kbCompleteBasketballSearch kbCreativeWriter100 kbMMStrauss kbMMSchubert kbMMStravinsky kbMMMozart100 kbAsimovSearch kbBookShelf1995 kbBookShelf1996 kbBookShelf1997 kbBookShelf1995Intro kbCompleteBaseball1994 kbCompleteBaseball1995 kbCompleteGardening kbDangerousCreatures kbDinosaurs100 kbExplorapediaNature100 kbExplorapediaPeople100 kbFineArtist100 kbAsimovUltimateRobot kbMusicCentral kbMusicalInst kbPJLeopard kbSoundBits kbWine100 kbWine100a kbWine200 kbWorldofFlight kbScholasticHuman kbArtGallery kbCompleteNBABasketball1994 kbEncartaEnCyc1996 kbEncartaEnCyc1997 kbEncartaEnCyc1997Del kbEncartaEnCyc1995Intro kbEncartaWorldAtlas1996 kbMusicCentral1996 kbMusicCentral1997 kbDoItYourself kbMSBSearch
	Version           : :1.0,1.0a,2.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
