---
title: "Logical Existence Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Logical Existence functoids, about Logical Existence functoids"
  - "Logical Existence functoids, properties"
ms.assetid: 2ce33c5d-8384-4b82-b929-add0e5519c53
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Logical Existence Functoid
Use the **Logical Existence** functoid ( ![](../core/media/logicalexistence.gif "logicalexistence")) to determine whether the **Record**, **Field Element**, or **Field Attribute** node that is linked to it exists in a particular input instance message.  
  
## Input  
 **Parameter 1:** A link from a **Record**, **Field Element**, or **Field Attribute** node in the source schema that may or may not exist in a particular input instance message.  
  
## Output  
 **Output 1:** The Boolean value **True** if the element or attribute that corresponds to the **Record**, **Field Element**, or **Field Attribute** node that is linked to this functoid exists in a particular input instance message; the Boolean value **False** otherwise.  
  
## Remarks  
 The node in the source schema to which this functoid is linked must be a node that corresponds to an actual element or attribute in an instance message.  
  
## See Also  
 [Logical Functoids Reference](../core/logical-functoids-reference.md)   
 [Logical Functoids](../core/logical-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)