---
title: "SNALinkTerminate2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29789ee6-c1b4-4b86-b03a-52271a183bbe
caps.latest.revision: 3
---
# SNALinkTerminate
The **SNALinkTerminate** function terminates the SNALink. The Base calls this function, when present, during service shutdown. This allows the DLL to free memory, release system resources (such as events), and close drivers.  
  
```  
VOID SNALinkTerminate(void);  
```  
  
## Remarks  
 This function must not send messages to other SNA components.