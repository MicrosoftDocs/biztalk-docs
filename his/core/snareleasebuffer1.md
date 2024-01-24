---
description: "Learn more about: SNAReleaseBuffer"
title: "SNAReleaseBuffer1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNAReleaseBuffer
The **SNAReleaseBuffer** function is called by an application to release a buffer.  
  
```  
VOID SNAReleaseBuffer(  
PTRBFHDR msgptr  
);  
```  
  
## Parameters  
 *msgptr*  
 Pointer to the buffer to be released.  
  
## Remarks  
 It is important that buffers are released after use. This is done automatically when a message is transmitted. For messages received, it is the responsibility of the application either to release or to reuse the buffer.  
  
 This function releases both the buffer header and any associated buffer elements. It is possible to release single elements from a buffer by using the function [SNAReleaseElement](../core/snareleaseelement1.md).
