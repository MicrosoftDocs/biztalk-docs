---
title: "Initialization (I-O Request Packets)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be4d1a64-6733-4740-b850-f9daa3e140bb
caps.latest.revision: 3
---
# Initialization (I/O Request Packets)
Device drivers under Windows should perform all initialization required at the start of day when they are loaded by Windows. Configuration information for device drivers is stored in the Configuration Registry under Windows. For more details, refer to the documentation supplied with the Windows Device Driver Kit.  
  
 The SNALinks for dumb cards are implemented by the following files:  
  
 SDLC SNALink  
 *SNAroot*\SYSTEM\IBMSDLC.DLL  
  
 X.25 SNALink  
 *SNAroot*\SYSTEM\IBMX25.DLL  
  
 To bind to one of these, an installation script should mention the appropriate DLL in the IHVDLL registry entry that the script creates for the link service.