---
title: "Base-DMOD and SNALink Entry Point Summary1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffaa5264-1dae-404b-a77c-c2b5f373d0b5
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Base/DMOD and SNALink Entry Point Summary
The following tables show entry points divided into the categories SNALink, buffer management, and Base/DMOD, and listed in alphabetic order within each category.  
  
## SNALink entry points  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNALinkDispatchProc](../Topic/SNALinkDispatchProc1.md)|Dispatcher.|  
|[SNALinkInitialize](../Topic/SNALinkInitialize1.md)|Initialize SNALink.|  
|[SNALinkTerminate](../Topic/SNALinkTerminate2.md)|Terminate SNALink.|  
|[SNALinkWorkProc](../Topic/SNALinkWorkProc2.md)|Work manager.|  
  
## Buffer management entry points  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNAGetBuffer](../Topic/SNAGetBuffer2.md)|Get buffer.|  
|[SNAGetElement](../Topic/SNAGetElement2.md)|Get buffer element.|  
|[SNAReleaseBuffer](../Topic/SNAReleaseBuffer2.md)|Release buffer.|  
|[SNAReleaseElement](../Topic/SNAReleaseElement2.md)|Release buffer element.|  
  
## Base/DMOD entry points  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNAGetLinkName](../Topic/SNAGetLinkName2.md)|Get the name of the SNALink.|  
|[SNASendAlert](../Topic/SNASendAlert2.md)|Send a preformatted NMVT alert to NetView.|  
|[SNASendMessage](../Topic/SNASendMessage2.md)|Send a message to the node.|  
  
 The following functions are defined in [SNALink Configuration Information](../core/snalink-configuration-information.md):  
  
|Entry point|Description|  
|-----------------|-----------------|  
|[SNAGetConfigValue](../Topic/SNAGetConfigValue1.md)|Get a named item of configuration information.|  
|[SNAGetSystemInfo](../Topic/SNAGetSystemInfo2.md)|Get [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] system information.|  
  
> [!NOTE]
>  Standard calling conventions [WINAPI] are used for all entry points including those provided by the IHV SNALink.  
  
 The format of buffer headers and elements is described in [Messages](../core/messages-snadis.md). The formats of individual messages contained in buffers are defined in [SNADIS Message Formats](../Topic/SNADIS%20Message%20Formats1.md).