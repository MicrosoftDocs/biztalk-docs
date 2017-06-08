---
title: "Fully Qualified Name (Map Item Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fully Qualified Name property [maps]"
ms.assetid: e1505231-f88a-4ff3-beba-2025964380d0
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Fully Qualified Name (Map Item Property)
Use the **Fully Qualified Name** property to examine the fully qualified name of the compiler-generated managed type that corresponds to a map.  
  
## Category  
 Advanced  
  
## Read-Only Value  
 A combination of the default values for the [Namespace](../core/namespace-map-item-property.md) and [Type Name](../core/type-name-map-item-property.md) properties.  
  
## Remarks  
 This property combines the **Namespace** and **Type Name** properties by using a "Namespace**.**TypeName" notation.  
  
 To avoid compilation errors, all items in a BizTalk project must have a unique value for their **Fully Qualified Name** property. Because the value of this property is created by concatenating the **Namespace** property, a period (.), and the **Type Name** property, you must make sure that the combination of the values you provide for these two properties is unique within the BizTalk project.