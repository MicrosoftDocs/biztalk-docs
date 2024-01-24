---
description: "Learn more about: Initialization (I/O Request Packets)"
title: "Initialization (I-O Request Packets)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Initialization (I/O Request Packets)
Device drivers under Windows should perform all initialization required at the start of day when they are loaded by Windows. Configuration information for device drivers is stored in the Configuration Registry under Windows. For more details, refer to the documentation supplied with the Windows Device Driver Kit.  
  
 The SNALinks for dumb cards are implemented by the following files:  
  
 SDLC SNALink  
 *SNAroot*\SYSTEM\IBMSDLC.DLL  
  
 X.25 SNALink  
 *SNAroot*\SYSTEM\IBMX25.DLL  
  
 To bind to one of these, an installation script should mention the appropriate DLL in the IHVDLL registry entry that the script creates for the link service.
