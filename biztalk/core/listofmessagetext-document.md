---
title: "listOfMessageText Document | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cross Reference Import tool, listOfMessageText document"
  - "xref_MessageText table"
ms.assetid: 4cd90d1f-aa32-4844-b7f9-206e5a001336
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# listOfMessageText Document
The **listOfMessageText** document contains data stored in the **xref_MessageText** SQL Server table. The document has the following structure:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<listOfMessageText lang="en-us">  
    <messageText code="INVALID_CREDIT">Invalid Credit '%1'</messageText>  
.  
.  
.  
</listOfMessageText>  
  
```  
  
 The document contains one or more **messageText** elements. The following table describes the parts of the document:  
  
|Element|Attribute|Description|  
|-------------|---------------|-----------------|  
|messageText||A parameterized string of up to 1000 characters containing the text of a message.|  
|messageText|Code|A string of up to 50 characters that must match one of the **code** values in the **listOfMessageDef** document.|  
  
## See Also  
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)   
 [listOfMessageDef Document](../core/listofmessagedef-document.md)