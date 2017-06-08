---
title: "CodeList Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.editor.codelist"
helpviewer_keywords: 
  - "BizTalk Editor, CodeList dialog box"
  - "CodeList dialog box [BizTalk Editor]"
ms.assetid: 1531ab63-8bd6-4f12-a64e-b72757131edb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# CodeList Dialog Box
Use the **CodeList** dialog box to select which of the entries that match your choice of reference number should be added to your schema as valid enumeration values for the data in the corresponding element or attribute in instance messages described by the schema being edited.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Value** column|Examine the possible enumeration values that correspond to the reference number set for the **CodeList** property of the selected **Field Element** or **Field Attribute** node.<br /><br /> The values in this column correspond to the **value** column (column 2) in the corresponding table in the Microsoft Access database specified in the **CodeList Database** of the **Schema** node.|  
|**Value** column check boxes|Select the check boxes for what you consider valid data for the corresponding element or attribute in instance messages described by the schema being edited.<br /><br /> For each check box you select an **enumeration** element will be added to the XSD representation of the schema with its **value** attribute set to the value next to the check box.|  
|**Description** column|Provides a description of each corresponding value selection, which is particularly useful when the value column entries are terse, unreadable codes.<br /><br /> The values in this column correspond to the **Desc** column (column 3) in the corresponding table in the Microsoft Office Access database specified in the **CodeList Database** of the **Schema** node.|  
  
## See Also  
 [CodeList (Node Property of All Schemas)](../core/codelist-node-property-of-all-schemas.md)   
 [CodeList Database (Node Property of All Schemas)](../core/codelist-database-node-property-of-all-schemas.md)