---
description: "Learn more about: sbpusend"
title: "sbpusend1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# sbpusend
The **sbpusend** function sends a message from an application to a partner on an LPI connection.  
  
## Syntax  
  
```  
  
VOID sbpusend(   
PTRBFHDR msgptr   
);  
```  
  
#### Parameters  
 *msgptr*  
 Pointer to the message to be sent.  
  
## Remarks  
 The message buffer is released after transmission by the Dynamic Access Module (DMOD). It cannot be accessed by the application again.  
  
 For an Open request message, the **destl** parameter can be zero. In this case, the Resource Locator will attempt to find a suitable destination for the Open message.
