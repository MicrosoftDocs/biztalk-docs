---
description: "Learn more about: Warning - Using Custom XSLT and Extension XML"
title: "Warning - Using Custom XSLT and Extension XML"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.warning.usingCustomXsltAndExtensionXML"
---
# Warning - Using Custom XSLT and Extension XML
**Error Code**  
  
 btm1035  
  
 **Explanation**  
  
 The presence of override values for the **Custom XSLT Path** and **Custom Extension XML** properties is controlling the output instance messages produced by this map, completely ignoring any mappings specified between the source and destination schemas. If this is intentional, you can ignore this warning.  
  
 One scenario in which this is valid is to use BizTalk Mapper to generate preliminary XSLT for the mapping, modify this XSLT by hand to meet specific additional requirements, and then specify the modified file as the value of the **Custom XSLT Path** property, thereby overriding the preliminary XSLT during subsequent mapping operations.  
  
 **User Action**  
  
 If you do not intend to override the mapping specified within this map, remove the override values for the **Custom XSLT Path** property and the **Custom Extension XML** property, as appropriate.
