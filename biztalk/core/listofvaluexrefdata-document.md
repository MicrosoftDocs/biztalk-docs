---
title: "listOfValueXRefData Document | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cross Reference Import tool, listOfValueXRefData document"
  - "xref_ValueXRefData table"
ms.assetid: 17d7a54b-3f7b-4217-90b0-49f8f2b4e48d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# listOfValueXRefData Document
The **listOfValueXRefData** document contains data stored in the **xref_ValueXRefData** SQL Server table. The document has the following structure:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<listOfValueXRefData>  
    <valueXRef name="Credit Term">  
        <appType name="ApplicationOne">  
            <appValue commonValue="Credit Term 1">001</appValue>  
            <appValue commonValue="Credit Term 2">002</appValue>  
            <appValue commonValue="Credit Term 3">003</appValue>  
            <appValue commonValue="Credit Term 4">004</appValue>  
        </appType>  
    </valueXRef>  
.  
.  
.  
</listOfValueXRefData>  
  
```  
  
 The document contains one or more **valueXRef** elements. The following table describes the parts of the document:  
  
|Element|Attribute|Description|  
|-------------|---------------|-----------------|  
|valueXRef||Contains one or more **appType** elements.|  
|valueXRef|Name|A string of up to 50 characters that must match one of the **name** values in the **listOfValueXRef** document.|  
|appType||Contains one or more **appValue** elements.|  
|appType|Name|A string of up to 50 characters that must match one of the **name** values in the **listOfAppType** document.|  
|appValue||A string of up to 50 characters that is mapped to the value of the **commonValue** attribute of the element.|  
|appValue|commonValue|A string of up to 50 characters that is mapped to the value of the element.|  
  
## See Also  
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)   
 [listOfValueXRef Document](../core/listofvaluexref-document.md)   
 [listOfAppType Document](../core/listofapptype-document.md)