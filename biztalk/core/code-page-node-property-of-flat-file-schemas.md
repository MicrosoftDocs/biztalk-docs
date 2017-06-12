---
title: "Code Page (Node Property of Flat File Schemas) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Code Page property [Flat File schemas]"
ms.assetid: 3ea69942-7642-4cd8-befe-63d170eafd4f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Code Page (Node Property of Flat File Schemas)
Use the **Code Page** property to specify the code page to use with an instance message.  
  
## Applies to Nodes of Type  
 [Schema](../core/schema-node-properties.md)  
  
## Category  
 Flat File  
  
## Allowed Values  
 Any of the code pages available in the drop-down list, or a number that corresponds to a code page not in the list.  
  
## Default Value  
 If no value is specified for the **Code Page** property, the default value is UTF-8. However, there are multiple other factors that play a role in determining the encoding scheme to use with an instance message. See remarks for more information.  
  
## XSD Persistence  
 As the value of the **codepage** (="NNNN") attribute of the **schema/annotation/appinfo/schemaInfo** element.  
  
## Remarks  
 You can examine and set this property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when you select the **Schema** node in BizTalk Editor and you have configured the **Flat File Extension** option for the **Schema Editor Extensions** property of that node.  
  
 The values that you enter for this property are not validated. Therefore, if you type a value that is not valid, it may cause inaccurate results.  
  
 There are multiple factors that play a role in determining how character encoding for a given instance message is handled, as follows:  
  
-   When disassembling a flat file instance message, the following algorithm is used to determine and preserve encoding information:  
  
    1.  If the "Charset" in the body part is set, use it.  
  
    2.  Otherwise, if the envelope (or document) schema specifies a code page, use it.  
  
    3.  Otherwise, if a byte order mark is present, use it.  
  
    4.  Otherwise, assume UTF-8.  
  
-   When assembling a flat file instance message, the following algorithm is used to determine the charset to use for decoding:  
  
    1.  If the "XMLNorm.TargetCharset" message context property is set, use it.  
  
    2.  Otherwise, if the "TargetCharset" assembler (design-time) property is set, use it.  
  
    3.  Otherwise, if the envelope (or document) schema specifies a code page, use it.  
  
    4.  Otherwise, if the "SourceCharset" message context property is set, use it.  
  
    5.  Otherwise, use UTF-8.  
  
## See Also  
 [Supplemental Node Properties for Flat File Schemas](../core/supplemental-node-properties-for-flat-file-schemas.md)