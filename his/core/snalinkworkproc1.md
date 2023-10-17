---
description: "Learn more about: SNALinkWorkProc"
title: "SNALinkWorkProc1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6640357-8b34-422e-b8cf-415ccf641915
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# SNALinkWorkProc
The **SNALinkWorkProc** function is the work manager function. The Base calls this function whenever the global Base event is triggered by the SNALink, or at least once every five seconds.  
  
```  
VOID SNALinkWorkProc(void);  
```  
  
## Remarks  
 This function can be used to perform any general processing required by the SNALink, in particular to process messages received from the link.
