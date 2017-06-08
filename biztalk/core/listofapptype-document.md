---
title: "listOfAppType Document | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cross Reference Import tool, listOfAppType document"
  - "xref_AppType table"
ms.assetid: 6ac0e2e8-5656-4a0b-87c7-a0dac590fc80
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# listOfAppType Document
The **listOfAppType** document contains data stored in the **xref_AppType** SQL Server table. The document has the following structure:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<listOfAppType>  
    <appType>  
        <name>ApplicationOne</name>  
    </appType>  
    <appType>  
        <name>ApplicationTwo</name>  
    </appType>  
    <appType>  
        <name>ApplicationThree</name>  
    </appType>  
    <appType>  
        <name>ApplicationFour</name>  
    </appType>  
</listOfAppType>  
  
```  
  
 The following table describes the elements of the document:  
  
|Element|Description|  
|-------------|-----------------|  
|appType|Contains a single **name** element.|  
|Name|A string of up to 50 characters that is the name of an application.|  
  
 The names in this document are placed in the **xref_AppType** SQL Server table where they are mapped to unique integers used as values in other tables.  
  
## See Also  
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)   
 [listOfAppInstance Document](../core/listofappinstance-document.md)