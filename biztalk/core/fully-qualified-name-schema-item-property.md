---
title: "Fully Qualified Name (Schema Item Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fully Qualified Name property, [schema item]"
  - "schemas, naming conventions"
  - "schema item properties, Fully Qualified Name property"
  - "schemas, files"
ms.assetid: 193a0312-661d-4cef-bd23-4aab346542ef
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Fully Qualified Name (Schema Item Property)
Use the **Fully Qualified Name** property to examine the compiler-generated fully qualified name of the managed type of the selected schema file.  
  
## Category  
 Advanced  
  
## Read-Only Value  
 The compiler-generated fully qualified name of the managed type associated with the selected schema file, produced by combining the [Namespace](../core/namespace-schema-item-property.md) and [Type Name](../core/type-name-schema-item-property.md) properties, separated by a period (.).  
  
## Remarks  
 You can examine this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a schema file in Solution Explorer.  
  
 This property is read-only.  
  
 To avoid compilation errors, all items in a BizTalk project must have a unique value for their **Fully Qualified Name** property. Because you create the value of this property by concatenating the **Namespace** property, a period (.), and the **Type Name** property, you must make sure that the values you provide for these two properties, when combined, are unique within the BizTalk project.  
  
## See Also  
 [Namespace (Schema Item Property)](../core/namespace-schema-item-property.md)   
 [Type Name (Schema Item Property)](../core/type-name-schema-item-property.md)