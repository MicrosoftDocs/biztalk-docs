---
title: "Imports Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.editor.imports"
helpviewer_keywords: 
  - "Imports dialog box [BizTalk Editor]"
  - "schemas, importing"
  - "importing, schemas"
  - "BizTalk Editor, Imports dialog box"
ms.assetid: e4b631b1-de82-4ff2-aff9-9cc88e6ac652
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Imports Dialog Box
Use the **Imports** dialog box to add XSD **import**, **include**, or **redefine** directives to your schema, enabling it to use and redefine schema definitions from another XSD schema.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Import new schema as**|Select the type of multischema XSD operation you want to perform: import, include, or redefine.|  
|**Add**|Open the **BizTalk Type Picker** dialog box so that you can select the schema to import, include, or redefine.|  
|**Delete schema button**<br /><br /> ![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete")|Remove a previously imported, included, or redefined schema.<br /><br /> This button is unavailable for any automatically imported schemas, such as XMLSchema from w3.org.|  
|**Edit namespace prefix button**<br /><br /> ![](../core/media/bts-editbutton.gif "bts_editbutton")|Edit (in place) the automatically generated namespace prefix associated with any schema that you have imported, included, or redefined.<br /><br /> You can also edit the prefix by double-clicking the prefix entry.|  
|**Prefix** column|Show the prefix associated with the corresponding namespace. For schemas that you import, include, or redefine, you can edit this prefix as described for ![](../core/media/bts-editbutton.gif "bts_editbutton").|  
|**Namespace** column|Show the namespace URI associated with the corresponding schema.|  
|**Location** column|Show the relative file location of the corresponding schema.|  
|**Import Type** column|Show the type of multischema XSD operation associated with the corresponding schema for schemas that you import, include, or redefine.|  
  
## See Also  
 [Schemas That Use Other Schemas](../core/schemas-that-use-other-schemas.md)