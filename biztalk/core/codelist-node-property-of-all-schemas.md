---
title: "CodeList (Node Property of All Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CodeList property [schemas]"
ms.assetid: cdc08af6-04d9-40a0-bdbf-65598ad8b677
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CodeList (Node Property of All Schemas)
Use the **CodeList** property to define the reference number for the code list to use with the selected **Field Element** or **Field Attribute** node, and to access the **CodeList** dialog box in which you select the code list values to be set as enumeration values for this node.  
  
## Applies to Nodes of Type  
 [Field Element](../core/field-element-node-properties.md), [Field Attribute](../core/field-attribute-node-properties.md)  
  
## Category  
 BizTalk  
  
## Allowed Values  
 A numeric value that occurs in the **Code** column in one or more rows in a table in the Access database specified by the [CodeList Database](../core/codelist-database-node-property-of-all-schemas.md) property of the **Schema** node for the schema being edited. The name of the table is a combination of the [Standard](../core/standard-node-property-of-all-schemas.md) and [Standard Version](../core/standard-version-node-property-of-all-schemas.md) properties of the **Schema** node, separated by an underscore (_) character.  
  
 For example, if you have set the **Standard** property of the **Schema** node to "XML" and the **Standard Version** property to "MyVersion1", then the Access database specified by the **CodeList Database** property must have a table named "XML_MyVersion1".  
  
 This table must have three columns, typically named "Code", "Value", and "Desc". The first column identifies rows that are related to one another, where each such row provides one of the enumeration choices that may potentially be allowed for the data that corresponds to the selected **Field Element** or **Field Attribute** node.  
  
## Default Value  
 None.  
  
## XSD Persistence  
 The reference value is persisted as the value of the **codelist** attribute of:  
  
-   For **Field Element** nodes, the **element/annotation/appinfo/fieldInfo** annotation element.  
  
-   For **Field Attribute** nodes, the **attribute/annotation/appinfo/fieldInfo** annotation element.  
  
 The actual chosen codelist enumeration choices are persisted as one **enumeration** element for each row chosen using the **CodeList** dialog box, where the **value** attribute of each **enumeration** element is set to the string in the Value column of the corresponding row in the specified Access database table.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select a **Field Element** or **Field Attribute** node in BizTalk Editor and you have set its **Derived By** property to **Restriction**.  
  
> [!NOTE]
>  The **CodeList** and **CodeList Database** properties are used at design time only and are persisted in the XSD as corresponding settings for the **Enumeration** property. At run time, all values are verified against the **Enumeration** property only.  
  
 You must configure this property in conjunction with the **CodeList Database** property of the **Schema** node.  
  
 There are four separate steps in setting this property:  
  
1.  For the **Schema** node, verify that the **CodeList Database**, **Standard**, and **Standard Version** properties are set correctly for the Microsoft Access database in which your code list values are stored.  
  
2.  For the selected **Field Element** or **Field Attribute** node, set the **Derived By** property to **Restriction**. The **CodeList** property will not be enabled until you perform this step.  
  
3.  Type a value into the **CodeList Database** property. This value is typically an integer, but can be any string that does not contain spaces. Whatever the value, it should occur one or more times in the **Code** column (the first column) of an Access database table, where the name of the table is a concatenation of the **Standard** property value, an underscore (_) character, and the **Standard Version** property value, and the database file is specified using the **CodeList Database** property (the **Standard**, **Standard Version**, and **CodeList Database** properties are all properties of the **Schema** node).  
  
4.  Click the ellipsis (**...**) button located to the right of the **CodeList** property value field to open the **CodeList** dialog box. Using the check boxes in this dialog box, select the values that you want to allow as legal values for the instance message data that corresponds to the selected **Field Element** or **Field Attribute** node.  
  
 For a given **Field Element** or **Field Attribute** node, do not use both the **Enumeration** property and the **CodeList** property. Using the latter property can result in values entered using the former property to be overwritten.  
  
 For conceptual information about working with code lists in BizTalk Editor, see [Code List Management](../core/code-list-management.md).  
  
## See Also  
 [Node Properties of All Schemas](../core/node-properties-of-all-schemas.md)