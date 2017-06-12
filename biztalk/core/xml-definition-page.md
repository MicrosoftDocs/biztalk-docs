---
title: "XML Definition Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.bre.xml"
helpviewer_keywords: 
  - "Business Rule Composer, XML Definition page"
  - "XML Definition page [Business Rule Composer]"
ms.assetid: 36e41aca-e4e1-4d8c-bf35-13498f098023
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Definition Page
Use the **XML Definition** page to specify a definition for an XML document element or attribute.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Definition name**|Type a definition name that is unique within the vocabulary version.|  
|**Definition description**|Type a description for the definition.|  
|**Document type**|Specify the fact type for the XML document. If your policy will be called by a BizTalk orchestration, use the BizTalk message fully qualified type.|  
|**Instance ID**|Specify the instance identifier of the XML document, so that you can distinguish it when comparing two or more facts based on the same XML element or attribute.|  
|**Display name**|Specify a name for the vocabulary definition for display in rule definitions.|  
|**Perform "Set" Operation**|Specify that the definition is used as an action to assign a value to the XML element or attribute.|  
|**Perform "Get" Operation**|Specify that the definition is used as a function to retrieve a value from the XML element or attribute.|  
|**Type**|Select the .NET type for the definition.|  
|**XPath Selector**|Type the XPath to the XML record, element, or attribute to be selected. By default this will be the record XPath obtained from the schema.|  
|**XPath Field**|Type the XPath to the XML element or attribute to be selected. By default this will be the relative path from the XPath Selector obtained from the schema.|  
  
## See Also  
 [How to Create Vocabulary Definitions](../core/how-to-create-vocabulary-definitions.md)   
 [Windows of the Business Rule Composer](../core/windows-of-the-business-rule-composer.md)