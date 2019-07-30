---
title: "SNAGetLinkName1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffa740d8-8a7f-4295-84b4-decff6890673
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
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