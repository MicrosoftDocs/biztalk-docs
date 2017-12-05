---
title: "Base-DMOD and SNALink Entry Point Summary1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffaa5264-1dae-404b-a77c-c2b5f373d0b5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Base/DMOD and SNALink Entry Point Summary
The following tables show entry points divided into the categories SNALink, buffer management, and Base/DMOD, and listed in alphabetic order within each category.  
  
## SNALink entry points  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNALinkDispatchProc](../core/snalinkdispatchproc1.md)|Dispatcher.|  
|[SNALinkInitialize](../core/snalinkinitialize1.md)|Initialize SNALink.|  
|[SNALinkTerminate](../core/snalinkterminate2.md)|Terminate SNALink.|  
|[SNALinkWorkProc](../core/snalinkworkproc2.md)|Work manager.|  
  
## Buffer management entry points  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNAGetBuffer](../core/snagetbuffer2.md)|Get buffer.|  
|[SNAGetElement](../core/snagetelement2.md)|Get buffer element.|  
|[SNAReleaseBuffer](../core/snareleasebuffer2.md)|Release buffer.|  
|[SNAReleaseElement](../core/snareleaseelement2.md)|Release buffer element.|  
  
## Base/DMOD entry points  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNAGetLinkName](../core/snagetlinkname2.md)|Get the name of the SNALink.|  
|[SNASendAlert](../core/snasendalert2.md)|Send a preformatted NMVT alert to NetView.|  
|[SNASendMessage](../core/snasendmessage2.md)|Send a message to the node.|  
  
 The following functions are defined in [SNALink Configuration Information](../core/snalink-configuration-information1.md):  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNAGetConfigValue](../core/snagetconfigvalue1.md)|Get a named item of configuration information.|  
|[SNAGetSystemInfo](../core/snagetsysteminfo2.md)|Get [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] system information.|  
  
> [!NOTE]
>  Standard calling conventions [WINAPI] are used for all entry points including those provided by the IHV SNALink.  
  
 The format of buffer headers and elements is described in [Messages](../core/messages-snadis-1.md). The formats of individual messages contained in buffers are defined in [SNADIS Message Formats](../core/snadis-message-formats1.md).