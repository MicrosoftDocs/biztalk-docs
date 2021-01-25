---
description: "Learn more about: RetractByType"
title: "RetractByType | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RetractByType function [Business Rules Engine], TypedXMLDocument"
  - "RetractByType function [Business Rules Engine]"
  - "RetractByType function [Business Rules Engine], .NET objects"
  - "RetractByType function [Business Rules Engine], TypedData table"
  - "RetractByType function [Business Rules Engine], DataConnection"
  - ".NET objects"
ms.assetid: e8867553-ee3c-46be-84cd-d5373eaf3337
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# RetractByType
The **RetractByType** function retracts all instances of a specified type in the working memory, whereas the **Retract**function retracts only specific items of a certain type. The following paragraphs describe how the **RetractByType** function works with entities of different types.  
  
## .NET Objects  
 All objects for a given class type are retracted from working memory. You simply drag the class from the .NET Classes fact pane into the **RetractByType** function.  
  
## TypedXmlDocument  
 All instances are retracted. This means that all **TypedXmlDocument**s with the same **DocumentType.Selector** are retracted. You should drag the appropriate node from the XML Schemas fact pane into the **RetractByType** function. Consistent with the **Retract** function, if you perform a **RetractByType** on the document root node, not only will all **TypedXmlDocuments** asserted with that **DocumentType** be retracted, but all child **TypedXmlDocuments** (**XmlNode**s in the tree hierarchy) associated with those parent **TypedXmlDocuments** will also be retracted.  
  
## TypedDataTable and DataConnection  
 **Retract** and **RetractByType** are equivalent for both **TypedDataTable** and **DataConnection**. Because **DataSetName.DataTableName** is a unique identifier for both types, there is only one instance in the engine at any point in time. As with **Retract**, you drag the table into the **RetractByType** function.  
  
## See Also  
 [Engine Control Functions](../core/engine-control-functions.md)
