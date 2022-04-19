---
description: "Learn more about: SNAReleaseBuffer"
title: "SNAReleaseBuffer1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8f8f2d8-f3a1-4af4-8d70-343a7441ab80
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
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
