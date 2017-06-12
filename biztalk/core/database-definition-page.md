---
title: "Database Definition Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.bre.database"
helpviewer_keywords: 
  - "Business Rule Composer, Database Definition page"
  - "Database Definition page [Business Rule Composer]"
ms.assetid: 23b8f76c-20e2-4ba8-8728-6dde4de6aa6f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Database Definition Page
Use the **Database Definition** page to specify a definition for a database table or a database table column.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Definition name**|Type a definition name that is unique within the vocabulary version.|  
|**Definition description**|Type a description for the definition.|  
|**Instance ID**|Specify the instance identifier of the database and column, so that you can distinguish two or more rows from the same table and data set in a rule definition.|  
|**Data type**|Select the .NET type for the definition from the drop-down list.|  
|**Display name**|Specify a name for the vocabulary definition for display in rule definitions.|  
|**Perform "Set" Operation**|Specify that the definition is used as an action to assign a value to the database table column.|  
|**Perform "Get" Operation**|Specify that the definition is used as a function to retrieve a value from the database table column.|  
|**Dataset**|Type the fact type of the database table. The default is the database name. Use unique names for your data sets when defining rules that compare data from distinct tables with the same schema.|  
|**Binding type**|Select the database binding type from the drop-down list. Use Data connection on a single table to optimize retrieval; the engine will create a SQL query at runtime.  Use Data table/data row if your binding applies to multiple queries; the application must prepopulate the table or row before it executes the policy.|  
  
## See Also  
 [How to Create Vocabulary Definitions](../core/how-to-create-vocabulary-definitions.md)   
 [Windows of the Business Rule Composer](../core/windows-of-the-business-rule-composer.md)