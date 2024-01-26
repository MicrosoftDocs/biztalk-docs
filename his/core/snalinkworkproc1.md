---
description: "Learn more about: SNALinkWorkProc"
title: "SNALinkWorkProc1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNALinkWorkProc
The **SNALinkWorkProc** function is the work manager function. The Base calls this function whenever the global Base event is triggered by the SNALink, or at least once every five seconds.  
  
```  
VOID SNALinkWorkProc(void);  
```  
  
## Remarks  
 This function can be used to perform any general processing required by the SNALink, in particular to process messages received from the link.
