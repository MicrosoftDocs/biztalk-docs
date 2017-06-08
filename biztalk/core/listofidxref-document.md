---
title: "listOfIDXRef Document | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cross Reference Import tool, listOfIDXRef document"
  - "xref_IDXRef table"
ms.assetid: cb319c04-aac1-4281-9585-30bcb996ece3
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# listOfIDXRef Document
The **listOfIDXRef** document contains data stored in the **xref_IDXRef** SQL Server table. The document has the following structure:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<listOfIDXRef>  
    <idXRef>  
        <name>Customer</name>  
    </idXRef>  
    <idXRef>  
        <name>Order</name>  
    </idXRef>  
    <idXRef>  
        <name>Contact</name>  
    </idXRef>  
    <idXRef>  
        <name>Payment</name>  
    </idXRef>  
</listOfIDXRef>  
  
```  
  
 The following table describes the elements of the document:  
  
|Element|Description|  
|-------------|-----------------|  
|idXRef|Contains a **name** element.|  
|Name|A string of up to 50 characters indicating the object type.|  
  
 The **name** values in this document are placed in the **xref_IDXRef** SQL Server table where they are mapped to unique integers used as values in other tables.  
  
## See Also  
 [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)   
 [listOfIDXRefData Document](../core/listofidxrefdata-document.md)