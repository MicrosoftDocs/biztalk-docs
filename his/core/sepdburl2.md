---
description: "Learn more about: sepdburl"
title: "sepdburl2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# sepdburl
The application calls the **sepdburl** function to release a buffer.  
  
## Syntax  
  
```  
  
VOID sepdburl(  
PTRBFHDR msgptr  
);  
```  
  
#### Parameters  
 *msgptr*  
 Pointer to the buffer to be released.  
  
## Remarks  
 It is important that buffers are released after use. This is done automatically when a message is transmitted. For messages received, it is the responsibility of the application to either release or reuse the buffer.  
  
 This function releases both the buffer header and any associated buffer elements. It is possible to release single elements from a buffer by using the function [sbpiberl](../core/sbpiberl2.md).
