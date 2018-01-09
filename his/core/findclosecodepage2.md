---
title: "FindCloseCodePage2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45a4f0d0-e1f2-4d30-ae35-798dd5bbedb7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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
  
 SNANLS supports this function on [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].