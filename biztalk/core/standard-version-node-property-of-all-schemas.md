---
title: "Standard Version (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Standard Version property [schemas]"
ms.assetid: bb9c08b2-8cf1-4263-acaf-861c58f33c22
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Standard Version (Node Property of All Schemas)
Use the **Standard Version** property to qualify the version of the instance message format and/or syntax that you established using the [Standard](../core/standard-node-property-of-all-schemas.md) property, if appropriate.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Reference  
  
## Allowed Values  
 Any string, although it is most often a version string of some sort that is associated with the value set for the **Standard** property.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the **standards_version** attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Schema** node in BizTalk Editor.  
  
 An example of setting this property is when the standard is X12, you might set this property to "004010", or if the standard is EDIFACT, you might set this property to "D97B".  
  
 If you intend to use the CodeList feature, you should avoid using the period character (".") in the string you provide for this property. For additional information about this restriction, see [CodeList (Node Property of All Schemas)](../core/codelist-node-property-of-all-schemas.md) and [CodeList Database (Node Property of All Schemas)](../core/codelist-database-node-property-of-all-schemas.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)