---
description: "Learn more about: Promoting Properties"
title: "Promoting Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "properties, promoting"
  - "promoting properties"
  - "promoting properties, about promoting properties"
ms.assetid: e1825028-7dd9-4eae-a383-4db12a83a402
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Promoting Properties
Promotion of properties involves either promoting **Field Element** or **Field Attribute** nodes in a schema to be **Distinguished Fields** or **Property Fields**. You can also promote **Record** nodes as **Property Fields** if they have simple content (**Content Type** property of the **Record** node set to **SimpleContent**). This section provides step-by-step instructions for promoting nodes as either **Distinguished Fields** or as **Property Fields**.  
  
 To promote a **Record** (with simple content), **Field Element**, or **Field Attribute** node as a **Property Field**, you may first define a special type of schema called a property schema. Property schemas define an unstructured set of **Field Element** nodes into which you promote **Record** (with simple content), **Field Element**, or **Field Attribute** nodes. For step-by-step instructions for creating a property schema, see [How to Create Property Schemas](../core/how-to-create-property-schemas.md).  
  
 Alternatively, you can use the **Quick Promotion** feature, which will automatically create and update a single property schema whenever you promote a new **Field Element**, **Field Attribute**, or **Record** (with simple content) node.  
  
> [!NOTE]
>  You can promote a field as both a **Distinguished Field** and a **Property Field**.  
  
> [!NOTE]
>  The **Quick Promotion** feature modifies the property schema by inserting a new property with the name of the promoted node.  
  
> [!IMPORTANT]
>  Do not move or rename a field in the schema once you have promoted it. When you move or rename a schema field, BizTalk Editor does not update the XPath defining the location of the promoted field.  
  
## XSD and CLR Data Types  
 In some places, such as in property promotion, XSD data types are promoted to Common Language Runtime (CLR) data types. The following table shows the XSD data types that can be promoted and the corresponding CLR data types.  
  
|XSD Data Type|CLR Data Type|  
|-------------------|-------------------|  
|anyURI|String|  
|Boolean|Boolean|  
|Byte|sbyte|  
|Date|DateTime|  
|dateTime|DateTime|  
|Decimal|Decimal|  
|Double|Double|  
|ENTITY|String|  
|Float|Single|  
|gDay|DateTime|  
|gMonth|DateTime|  
|gMonthDay|DateTime|  
|gYear|DateTime|  
|gYearMonth|DateTime|  
|ID|String|  
|IDREF|String|  
|Int|Int32|  
|Integer|Decimal|  
|Language|String|  
|Name|String|  
|NCName|String|  
|negativeInteger|Decimal|  
|NMTOKEN|String|  
|nonNegativeInteger|Decimal|  
|nonPositiveInteger|Decimal|  
|normalizedString|String|  
|NOTATION|String|  
|positiveInteger|Decimal|  
|QName|String|  
|Short|Int16|  
|String|String|  
|Time|DateTime|  
|Token|String|  
|unsignedByte|Byte|  
|unsignedInt|UInt32|  
|unsignedShort|UInt16|  
  
> [!NOTE]
>  XSD Data Type of base64Binary, duration, ENTITES, hexBinary, IDREFS, long, NMTOKENS, and unsignedLong are not supported for promotion.  
  
## Limitations for Promoting Properties  
 When promoting properties, consider the following:  
  
-   Promoted properties are limited to 256 characters in length while written properties have no length limitation.  
  
-   Promoted properties are used in message routing and are limited in size for reasons of efficiency in comparison and storage. While written properties have no hard limits on size, using excessively large values in the context will have an impact on performance, because those values must still be processed and passed with the message. Distinguished Fields are the examples of written properties.  
  
-   Record nodes can never be promoted as **Distinguished Fields**.  
  
-   Promoted properties are restricted to non-repeating elements/attributes.  
  
-   Do not promote fields belonging to the same root node to the same property. Such promotions produce compilation or deployment errors.  
  
-   Within a message context, there are some properties that are not available since they are not promoted.  The BTS.ReceiveLocationName property is one such property. If you can add a new property schema or a new BizTalk Server project to your development it is possible to access this property from within an orchestration.  
  
     Property values are identified by the property target namespace and property name.  The following example shows how to access the receive location in code.  
  
     `string receiveLocationName =       pInMsg.Context.Read("ReceiveLocationName", sysNamespace);`  
  
## In This Section  
  
-   [How to Open the Promote Properties Dialog Box](../core/how-to-open-the-promote-properties-dialog-box.md)  
  
-   [How to Copy Data to the Message Context as Distinguished Fields](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)  
  
-   [How to Copy Data to the Message Context as Property Fields](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)
