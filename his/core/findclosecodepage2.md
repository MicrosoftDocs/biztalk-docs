---
description: "Learn more about: FindCloseCodePage"
title: "FindCloseCodePage2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FindCloseCodePage
The SNA National Language Support (SNANLS) **FindCloseCodePage** function closes the handle allocated by a call to the **FindFirstCodePage** function.  
  
## Syntax  
  
```  
  
BOOL WINAPI FindCloseCodePage(   
        const HANDLEhInfo  
);  
```  
  
#### Parameters  
 *hInfo*  
 Supplied parameter. The handle allocated and returned using **FindFirstCodePage**.  
  
## Return Value  
 The **FindCloseCodePage** function returns **TRUE** on success, otherwise the returned value on failure is **FALSE**.  
  
## Remarks  
 The *hInfo* parameter passed to this function is the handle returned from a previous call to the **FindFirstCodePage** function.  
  
 SNANLS supports this function on Host Integration Server.
