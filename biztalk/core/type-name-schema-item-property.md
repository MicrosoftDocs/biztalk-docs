---
title: "Type Name (Schema Item Property) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schema item properties, Type Name property"
  - "schemas, naming conventions"
  - "Type Name property [schema item]"
  - "schemas, files"
ms.assetid: f8a7d4d5-52c6-4df9-820b-b81358b412ab
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Type Name (Schema Item Property)
Use the **Type Name** property to examine and set the name of the managed type associated with the selected schema file.  
  
## Category  
 Advanced  
  
## Allowed Values  
 Any valid .NET class name string that is not reserved in C# or by BizTalk Server and is different than the value you have set for the **Namespace** property.  
  
## Default Value  
 The name of the schema file when the schema was first created, without the .xsd extension and with space characters replaced by underscore (_) characters.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a schema file in Solution Explorer.  
  
 To avoid compilation errors, you ensure sure that the value of the [Fully Qualified Name](../core/fully-qualified-name-schema-item-property.md) property (created by concatenating the value of the [Namespace](../core/namespace-schema-item-property.md) property, a period (.) character, and the value of this property) is unique throughout the BizTalk project.  
  
 Because the period (.) character has a special meaning in C#, avoid using it in type name values. For additional information about restrictions that apply to the values you can set for this property, see the remarks section of [Namespace (Schema Item Property)](../core/namespace-schema-item-property.md).  
  
## See Also  
 [Namespace (Schema Item Property)](../core/namespace-schema-item-property.md)   
 [Fully Qualified Name (Schema Item Property)](../core/fully-qualified-name-schema-item-property.md)