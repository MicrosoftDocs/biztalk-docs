---
title: "Database Functoids Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "functoid types, Database"
  - "Database functoids, about Database functoids"
  - "Database functoids, properties"
ms.assetid: fcd72f31-d451-43fb-aa2a-23e42b0a0985
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Database Functoids Reference
Use **Database** functoids to extract data from a database for use in an output instance message.  
  
 Database functoids fall into two categories. The first category consists of the **Database Lookup**, **Error Return**, and **Value Extractor** functoids, which are designed for general purpose retrieval of database values using Microsoft ActiveX Data Objects (ADO) recordsets. The second category consists of the **Format****Message**, **Get Application ID**, **Get Application Value**, **Get Common ID**, **Get Common Value**, **Remove Application ID**, and **Set Common ID** functoids, which correspond to the methods of the **CrossReferencing** class of the **Microsoft.BizTalk.CrossReferencing** API.  
  
> [!NOTE]
>  Unlike other functoids, which are written in C#, the first category of **Database** functoids (**Database Lookup**, **Error Return**, and **Value Extractor**) are not accessible from inline script that is run by using the **Scripting** functoid. This restriction is not true of the second category of **Database** functoids (that correspond to the methods of the **CrossReferencing** class).  
  
 The **Cross Referencing** functoids—**Format Message**, **Get Application ID**, **Get Application Value**, **Get Common ID**, **Get Common Value**, **Remove Application ID**, and **Set Common ID**—look for data in specific SQL Server tables. For more information about how populate those tables and the structure of the input files, see [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md).  
  
 For conceptual information about **Database**functoids, see [Database Functoids](../core/database-functoids.md).  
  
 The following table shows the functoids in the **Database** category.  
  
|Database functoid|Description|  
|-----------------------|-----------------|  
|![](../core/media/dblookup.gif "dblookup") [Database Lookup](../core/database-lookup-functoid.md)|Retrieves a row from a database table as an ADO recordset.|  
|![](../core/media/dberrorextract.gif "dberrorextract") [Error Return](../core/error-return-functoid.md)|Captures error information, such as database connection failures, that occur during run time.|  
|![](../core/media/formatmessage.gif "formatmessage") [Format Message](../core/format-message-functoid.md)|Returns a formatted and localized string using argument substitution and, potentially, ID and value cross referencing.|  
|![](../core/media/getapplicationid.gif "getapplicationid") [Get Application ID](../core/get-application-id-functoid.md)|Retrieves an identifier for an application object.|  
|![](../core/media/getapplicationvalue.gif "getapplicationvalue") [Get Application Value](../core/get-application-value-functoid.md)|Retrieves an application value.|  
|![](../core/media/getcommonid.gif "getcommonid") [Get Common ID](../core/get-common-id-functoid.md)|Retrieves an identifier for a common object.|  
|![](../core/media/getcommonvalue.gif "getcommonvalue") [Get Common Value](../core/get-common-value-functoid.md)|Retrieves a common value.|  
|![](../core/media/getapplicationid.gif "getapplicationid") [Remove Application ID](../core/remove-application-id.md)|Removes the identifier for an application object.|  
|![](../core/media/setcommonid.gif "setcommonid") [Set Common ID](../core/set-common-id-functoid.md)|Sets and returns an identifier for a common object.|  
|![](../core/media/dbvalueextract.gif "dbvalueextract") [Value Extractor](../core/value-extractor-functoid.md)|Extracts the value from a specified column in an ADO recordset returned by the **Database Lookup** functoid.|  
  
 This section also contains:  
  
-   [Importing Data for the Cross Referencing Functoids](../core/importing-data-for-the-cross-referencing-functoids.md)  
  
## See Also  
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)