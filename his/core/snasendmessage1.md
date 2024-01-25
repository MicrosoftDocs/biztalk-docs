---
description: "Learn more about: SNASendMessage"
title: "SNASendMessage1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNASendMessage
The **SNASendMessage** function is called by an application to send messages to other localities (in the case of an SNALink, the local 2.1 node).  
  
```  
VOID SNASendMessage(  
PTRBFHDR *msgptr  
);  
```  
  
## Parameters  
 *msgptr*  
 Pointer to message to be sent.  
  
## Remarks  
 The locality, partner, index (LPI) values on the message should be set up to reference the correct connection for the data to be passed.
