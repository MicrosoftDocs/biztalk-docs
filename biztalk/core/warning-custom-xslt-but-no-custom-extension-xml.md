---
description: "Learn more about: Warning - Custom XSLT but No Custom Extension XML"
title: "Warning - Custom XSLT but No Custom Extension XML | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.warning.customXsltButNoCustomExtensionXML"
ms.assetid: af008ac2-e9ae-4753-a5ba-bf4dbb711a4e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Warning - Custom XSLT but No Custom Extension XML
**Error Code**  
  
 btm1034  
  
 **Explanation**  
  
 The **Custom XSLT Path** property has been overridden without the **Custom Extension XML** property being overridden. If this is intentional, you can ignore this warning.  
  
 BizTalk Mapper will use the XSLT specified by the **Custom XSLT Path** property and generate a dummy Extension XML mapping file. If you make calls to external assemblies from within the provided custom XSLT, you must specify a file using the **Custom Extension XML** property that contains the prefix to assembly name mapping.  
  
 **User Action**  
  
 If the condition indicated by this warning was not intentional, either provide a compatible value for the **Custom Extension XML** property or remove the override value for the **Custom XSLT Path** property.
