---
title: "Default Value (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Default Value property [schemas]"
ms.assetid: 32fe94f4-7e71-456e-b55e-91a28e4a762c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Default Value (Node Property of All Schemas)
Use the **Default Value** property to specify the default value for the message instance field that corresponds to the selected **Field Element** or **Field Attribute** node.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 General  
  
## Allowed Values  
 Any value that conforms to the data type specified by the [Data Type](../core/data-type-node-property-of-all-schemas.md) property.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 As the value of the **default** attribute of the element that corresponds to the selected **Field Element** or **Field Attribute** node.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor.  
  
 You can configure this property with any valid XML data that is of the associated simple type.  
  
> [!NOTE]
>  Date and time data types, of which there are several, must conform to ISO 8601 formats. In brief, dates are expressed as **YYYY-MM-DD** and hours are expressed as **hh:mm:ss** using 24-hour notation. When they occur together, date and time values are separated by the "T" character: **YYYY:MM:DDThh:mm:ss**.  
  
 This property represents a standard XSD construct. For additional information about the corresponding XSD construct, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).  
  
 You cannot configure both the **Default Value** property and the **Fixed** property because it is prohibited by XSD.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)