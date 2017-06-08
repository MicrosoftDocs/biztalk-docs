---
title: "listOfAppInstance Document | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "xref_AppInstance table"
  - "Cross Reference Import tool, listOfAppInstance document"
ms.assetid: 831eaa54-facf-4528-921f-3af6a5e7fd6f
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# listOfAppInstance Document
The **listOfAppInstance** document contains data stored in the **xref_AppInstance** SQL Server table. The document has the following structure:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<listOfAppInstance>  
    <appInstance>  
        <instance>ApplicationOne_01</instance>  
        <type>ApplicationOne</type>  
    </appInstance>  
    <appInstance>  
        <instance>ApplicationOne_02</instance>  
        <type>ApplicationOne</type>  
    </appInstance>  
    <appInstance>  
        <instance>ApplicationTwo_01</instance>  
        <type>ApplicationTwo</type>  
    </appInstance>  
    <appInstance>  
        <instance>ApplicationThree_01</instance>  
        <type>ApplicationThree</type>  
    </appInstance>  
    <appInstance>  
        <instance>ApplicationFour_01</instance>  
        <type>ApplicationFour</type>  
    </appInstance>  
</listOfAppInstance>  
  
```  
  
 The following table describes the elements of the document:  
  
|Element|Description|  
|-------------|-----------------|  
|appInstance|Contains an **instance** element and a **type** element.|  
|Instance|A string of up to 50 characters that is an identifier for an instance of an application.|  
|Type|A string of up to 50 characters indicating the application type. The value must match one of the **name** elements entered in the **listOfAppType** document.|  
  
 The **instance** values in this document are placed in the **xref_AppInstance** SQL Server table where they are mapped to unique integers used as values in other tables.  
  
## See Also  
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)   
 [listOfAppType Document](../core/listofapptype-document.md)