---
title: "Additional Flat File Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c88ad2f-b5a8-46e6-b1b8-61ce6ba910d1
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Additional Flat File Properties

## Hidden properties
The following table lists additional flat file node properties that do not appear in the Schema Editor. Using these properties requires hand editing the schema file in a text editor.  

|Property|Values|Default Value|Description|  
|--------------|------------|-------------------|-----------------|  
|suppress_empty_nodes|**true** or **false**|**false**|Indicates whether or not to remove empty XML nodes after the parser generates XML instance data.|  
|generate_empty_nodes|**true** or **false**|**true**|Generate empty nodes for records that exist in the XML instance data.|  
|parser_optimization|**speed** or **complexity**|**speed**|Optimizing for speed decreases the parsing time but at the cost of dealing with some ambiguities in data. Optimizing for complexity handles a wider range of ambiguities but at the cost of processing speed.|  
|lookahead_depth|Any positive integer; zero (0) indicates infinite lookahead.|3|How far to look ahead for matching data.|  
|allow_early_termination|**true** or **false**|**false**|Indicates whether positional records can terminate early (**true**) or must contain data for all record fields (**false**).|  
|early_terminate_optional_fields|**true** or **false**|**false**|Enable early termination of optional trailing fields (**true**). If the existing schema without this annotation is opened in the BizTalk Editor, this annotation will be added to it with the default value set to (**false**). **Note:**  The early_terminate_optional_fields annotation only takes effect if the allow_early_termination is set to "true".|  

 All of these properties are attributes of the **/annotation/appinfo/schemaInfo** element.  

 When **parser_optimization** is set to **complexity**, you may have validation failures against a schema when there are many optional nodes in the same group or record. You may need to set **lookahead_depth** to zero (0) to avoid validation errors.  

## See Also  
- [Node Properties](../core/node-properties.md)   
- **Supplemental Node Properties for Flat File Schemas** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
