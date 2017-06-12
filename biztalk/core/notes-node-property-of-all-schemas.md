---
title: "Notes (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Notes property [schemas]"
ms.assetid: f193c04e-81f8-4460-b3d7-a25e6dd35f48
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Notes (Node Property of All Schemas)
Use the **Notes** property to enter notes, such as comments that are related to the business process, that you would like to make about the selected **Record**, **Field Element**, or **Field Attribute** node.  
  
## Applies to Nodes of Type  
 [Record](../core/record-node-properties.md), [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 BizTalk  
  
## Allowed Values  
 Any string, without a specific maximum limit. In practice, however, it is not advisable to burden your schemas with very large notes.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 For **Record** nodes, as the value of the **notes** attribute of the **element/annotation/appinfo/recordInfo** element.  
  
 For **Field Element** nodes, as the value of the **notes** attribute of the **element/annotation/appinfo/fieldInfo** element.  
  
 For **Field Attribute** nodes, as the value of the **notes** attribute of the **attribute/annotation/appinfo/fieldInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Record**, **Field Element**, or **Field Attribute** node in BizTalk Editor.  
  
 You can type notes directly into the **Notes** property value field, or you can click the ellipsis (**...**) button located to the right of the **Notes** property value field to open the **Notes** dialog box, in which you can type your notes into a multi-line edit box.  
  
 For example, you might want to provide a note when a particular element in an instance message contains confidential information. You might then want to add note to the corresponding **Record** or **Field Element** node that says:  
  
 "The data in this record is confidential. Do not distribute it outside this company."  
  
 Such a note might prevent someone creating a map with this schema from inadvertently mapping that data into instance messages that circulate outside the company.  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)