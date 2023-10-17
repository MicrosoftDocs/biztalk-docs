---
description: "Learn more about: SNALinkTerminate"
title: "SNALinkTerminate1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0360ef9-c993-49da-84cc-6600340cb1d1
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# SNALinkTerminate
The **SNALinkTerminate** function terminates the SNALink. The Base calls this function, when present, during service shutdown. This allows the DLL to free memory, release system resources (such as events), and close drivers.  
  
```  
VOID SNALinkTerminate(void);  
```  
  
## Remarks  
 This function must not send messages to other SNA components.
