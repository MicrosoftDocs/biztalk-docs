---
description: "Learn more about: Base/DMOD and SNALink Entry Point Summary"
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
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Base/DMOD and SNALink Entry Point Summary
The following tables show entry points divided into the categories SNALink, buffer management, and Base/DMOD, and listed in alphabetic order within each category.  
  
## SNALink entry points  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNALinkDispatchProc](./snalinkdispatchproc2.md)|Dispatcher.|  
|[SNALinkInitialize](./snalinkinitialize2.md)|Initialize SNALink.|  
|[SNALinkTerminate](./snalinkterminate1.md)|Terminate SNALink.|  
|[SNALinkWorkProc](./snalinkworkproc1.md)|Work manager.|  
  
## Buffer management entry points  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNAGetBuffer](./snagetbuffer1.md)|Get buffer.|  
|[SNAGetElement](./snagetelement1.md)|Get buffer element.|  
|[SNAReleaseBuffer](./snareleasebuffer1.md)|Release buffer.|  
|[SNAReleaseElement](./snareleaseelement1.md)|Release buffer element.|  
  
## Base/DMOD entry points  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNAGetLinkName](./snagetlinkname1.md)|Get the name of the SNALink.|  
|[SNASendAlert](./snasendalert1.md)|Send a preformatted NMVT alert to NetView.|  
|[SNASendMessage](./snasendmessage1.md)|Send a message to the node.|  
  
 The following functions are defined in [SNALink Configuration Information](../core/snalink-configuration-information1.md):  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNAGetConfigValue](./snagetconfigvalue2.md)|Get a named item of configuration information.|  
|[SNAGetSystemInfo](./snagetsysteminfo1.md)|Get Host Integration Server system information.|  
  
> [!NOTE]
>  Standard calling conventions [WINAPI] are used for all entry points including those provided by the IHV SNALink.  
  
 The format of buffer headers and elements is described in [Messages](../core/messages-snadis-1.md). The formats of individual messages contained in buffers are defined in [SNADIS Message Formats](./snadis-message-formats2.md).
