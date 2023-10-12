---
description: "Learn more about: SNALinkTerminate"
title: "SNALinkTerminate1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNALinkTerminate
The **SNALinkTerminate** function terminates the SNALink. The Base calls this function, when present, during service shutdown. This allows the DLL to free memory, release system resources (such as events), and close drivers.  
  
```  
VOID SNALinkTerminate(void);  
```  
  
## Remarks  
 This function must not send messages to other SNA components.
