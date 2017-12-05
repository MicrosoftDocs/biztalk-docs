---
title: "SNALinkWorkProc2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 08b01d85-fef4-4109-a4b2-2c3f37db9993
caps.latest.revision: 3
---
# SNALinkWorkProc
The **SNALinkWorkProc** function is the work manager function. The Base calls this function whenever the global Base event is triggered by the SNALink, or at least once every five seconds.  
  
```  
VOID SNALinkWorkProc(void);  
```  
  
## Remarks  
 This function can be used to perform any general processing required by the SNALink, in particular to process messages received from the link.