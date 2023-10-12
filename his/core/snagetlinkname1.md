---
description: "Learn more about: SNAGetLinkName"
title: "SNAGetLinkName1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
