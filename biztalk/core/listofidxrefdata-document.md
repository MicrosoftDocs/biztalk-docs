---
title: "listOfIDXRefData Document | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cross Reference Import tool, listOfIDXRefData document"
  - "xref_IDXRefData table"
ms.assetid: aa95183a-6d95-4655-89d3-f89501801c00
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# listOfIDXRefData Document
The **listOfIDXRefData** document contains data stored in the **xref_IDXRefData** SQL Server table. The document has the following structure:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<listOfIDXRefData>  
    <idXRef name="Customer">  
        <appInstance name="ApplicationOne_01">  
            <appID commonID="ADDRESS6">LOCALADDRESS</appID>  
            <appID commonID="ADDRESS7">NON-LOCALADDRESS</appID>  
        </appInstance>  
    </idXRef>  
.  
.  
.  
</listOfIDXRefData>  
  
```  
  
 The document consists of one or more **idXRef** elements. The following table describes the elements of the document:  
  
|Element|Attribute|Description|  
|-------------|---------------|-----------------|  
|idXRef||Contains one or more **appInstance** elements.|  
|idXRef|Name|A string of up to 50 characters matching one of the **name** elements in the **listOfIDXRef** document.|  
|appInstance||Contains one or more **appID** elements.|  
|appInstance|Name|A string of up to 50 characters matching one of the **instance** elements in the **listOfAppInstance** document.|  
|appID||Contains a string of up to 50 characters specific to the application and that is mapped to the corresponding **commonID** value.|  
|appID|commonID|A string of up to 50 characters that is mapped to the value of **appID**.|  
  
## See Also  
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)   
 [listOfAppInstance Document](../core/listofappinstance-document.md)   
 [listOfIDXRef Document](../core/listofidxref-document.md)