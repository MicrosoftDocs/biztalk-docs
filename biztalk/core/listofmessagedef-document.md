---
title: "listOfMessageDef Document | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "xref_MessageArgument table"
  - "Cross Reference Import tool, listOfMessageDef document"
  - "xref_MessageDef table"
ms.assetid: 0f2787cf-7294-4f13-9b72-fef76f91a335
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# listOfMessageDef Document
The **listOfMessageDef** document contains data stored in the **xref_MessageDef** and **xref_MessageArgument** SQL Server tables. The document has the following structure:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<listOfMessageDef>  
    <messageDef>  
        <code>INVALID_CREDIT</code>  
        <description>The credit code is not valid.</description>  
        <argumentName idXRefName="Credit Type">Credit Type</argumentName>  
    </messageDef>  
.  
.  
.  
</listOfMessageDef>  
  
```  
  
 The document contains one or more **messageDef** elements. The following table describes the parts of the document:  
  
|Element|Attribute|Description|  
|-------------|---------------|-----------------|  
|messageDef||Contains **code**, **description**, and **argumentName** elements.|  
|code||A string of up to 50 characters that uniquely identifies the message.|  
|description||A string of up to 1000 characters describing the message.|  
|argumentName||A string of up to 50 characters that is the name of the argument inserted in the message.|  
|argumentName|idXRefName|A string of up to 50 characters that must match one of the **idxRefName** values in the **listOfIDXRef** document.|  
  
 The **code** element is mapped to a unique identifier used as a value in other tables.  
  
## See Also  
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)   
 [listOfIDXRef Document](../core/listofidxref-document.md)   
 [listOfMessageText Document](../core/listofmessagetext-document.md)