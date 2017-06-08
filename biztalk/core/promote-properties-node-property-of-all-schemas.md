---
title: "Promote Properties (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Promote Properties property [schemas]"
ms.assetid: 85921875-6286-4abb-a3ca-838237ec46aa
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Promote Properties (Node Property of All Schemas)
Use the **Promote Properties** property to define the properties that you want to promote to the property context container and to import property schemas for use in conjunction with property promotion.  
  
## Applies to Nodes of Type  
 [Schema Node Properties](../core/schema-node-properties.md)  
  
## Category  
 BizTalk  
  
## Allowed Values  
 To set the values associated with this property, click the ellipsis (**...**) button located to the right of the property value field to open the **Promote Properties** dialog box.  
  
 Data in instance messages can be promoted as either property fields or distinguished fields. Distinguished fields are only accessible in BizTalk orchestrations. Property fields are accessible from a wide variety of BizTalk Server components and can be used for context-based routing. In order to use property fields, you must create or use an existing property schema that declares the appropriate property fields.  
  
 The values associated with property promotion, as established using the **Promote Properties** dialog box, are schema annotations that carry the following information, allowing the designated properties to be "copied" to the property context container when message processing begins, allowing easier access to their values by a variety of BizTalk Server components:  
  
-   For property field promotions, the namespace and property name of the corresponding property in a property schema, and the instance message XPath of the property to be promoted.  
  
-   For distinguished field promotions, the instance message XPath of the property to be promoted.  
  
 For conceptual and procedural information about property promotion, see [Ways to Use Message Content to Control Message Processing](../core/ways-to-use-message-content-to-control-message-processing.md). Also see [Promoting Properties](../core/promoting-properties.md).  
  
## XSD Persistence  
 Within the root **Record** node containing the node associated with the data to be promoted, as a **property** element within the **element/annotation/appinfo/recordInfo/properties** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor.  
  
 You can only promote a particular property in the schema in which the corresponding **Field Element** or **Field Attribute** node is defined, and not in any other schemas in which the definition is imported.  
  
 Property field promotion is subject to the following limitations:  
  
-   Promoting a string value that is longer than 256 characters in length may cause overflow exceptions at run-time.  
  
-   Promoting nodes of data type **xs:integer** that require more than 28 digits may cause overflow exceptions at run time (due to the internal use of the .NET data type **System.Decimal**, which has a 28-digit limit). You can work around this limitation by interpreting and promoting very large numeric values as strings, thereby increasing the effective limit to 256 digits.  
  
-   Promoting nodes of data type **xs:long** or **xs:unsignedLong** is not supported at run time and may lead to unexpected results. To avoid this issue, consider changing the data type of such promoted nodes to **xs:string**.  
  
 For conceptual information about promoting properties, see [Ways to Use Message Content to Control Message Processing](../core/ways-to-use-message-content-to-control-message-processing.md).  
  
 For information about the **Promote Properties** dialog box, see [How to Open the Promote Properties Dialog Box](../core/how-to-open-the-promote-properties-dialog-box.md).  
  
> [!CAUTION]
>  Do not promote system properties. Promotion of system properties, such as ReceivePortName, produces unpredictable behavior.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)