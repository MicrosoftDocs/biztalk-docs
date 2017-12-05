---
title: "SNAGetLinkName2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 991e8be5-f7b5-4ce9-87f6-c33b3babfbe9
caps.latest.revision: 3
---
# SNAGetLinkName
The SNALink can call the **SNAGetLinkName** function to obtain its configured SNALink name.  
  
```  
VOID SNAGetLinkName(  
VCHAR *linkname  
);  
```  
  
## Parameters  
 *linkname*  
 A pointer to a buffer where the NULL-terminated SNALink name is stored.  
  
## Remarks  
 The buffer should be at least nine bytes in length.