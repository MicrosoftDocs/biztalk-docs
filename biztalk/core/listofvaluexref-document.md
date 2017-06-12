---
title: "listOfValueXRef Document | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cross Reference Import tool, listOfValueXRef document"
  - "xref_ValueXRef table"
ms.assetid: a788e25b-b9ec-4273-813c-8294bbee7cce
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# listOfValueXRef Document
The **listOfValueXRef** document contains data stored in the **xref_ValueXRef** SQL Server table. The document has the following structure:  
  
```  
<?xml version = "1.0" encoding = "UTF-8"?>  
<listOfValueXRef>  
    <valueXRef>  
        <name>Country</name>  
    </valueXRef>  
    <valueXRef>  
        <name>Credit Term</name>  
    </valueXRef>  
    <valueXRef>  
        <name>Order Type</name>  
    </valueXRef>  
</listOfValueXRef>  
  
```  
  
 The following table describes the elements of the document:  
  
|Element|Description|  
|-------------|-----------------|  
|valueXRef|Contains a single **name** element.|  
|Name|A string of up to 50 characters.|  
  
 The **name** values in this document are placed in the **xref_ValueXRef** SQL Server table where they are mapped to unique integers used as values in other tables.  
  
## See Also  
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)   
 [listOfValueXRefData Document](../core/listofvaluexrefdata-document.md)