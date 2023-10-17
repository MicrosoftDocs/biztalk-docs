---
description: "Learn more about: EDI Message Structure"
title: "EDI Message Structure | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c9a0447-447f-483c-825d-547c06ad691e
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Message Structure
EDI messages consist of an envelope and a hierarchical series of structural elements. The envelope contains a set of headers and trailers, each set of which describes and contains a structural element. These structural elements are as follows:  
  
```  
Interchange  
   Group  
      Transaction set/message  
         Segment  
            Data Element  
               Sub Element  
```  
  
 The hierarchical structure of an EDI message enables transaction sets/messages and groups to be batched. Even if an interchange contains only one transaction set/message and only one group, that interchange is structured with the same basic structural elements that it would have if it were batched, with the exception that there would not be multiple transaction set/message or group elements.  
  
## In This Section  
  
-   [EDI Headers and Trailers](../core/edi-headers-and-trailers.md)  
  
-   [EDI Interchange Structural Element](../core/edi-interchange-structural-element.md)  
  
-   [EDI Group Structural Element](../core/edi-group-structural-element.md)  
  
-   [EDI Transaction Set-Message Structural Element](../core/edi-transaction-set-message-structural-element.md)  
  
-   [EDI Segment Structural Element](../core/edi-segment-structural-element.md)  
  
-   [EDI Data Element Structural Element](../core/edi-data-element-structural-element.md)
