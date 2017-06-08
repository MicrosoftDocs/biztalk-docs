---
title: "Set Management Database Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.tpe.database"
ms.assetid: b6efff59-1393-4ab9-8a27-592365a7edb6
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Set Management Database Dialog Box
Use the **Set Management Database** dialog box to specify the BizTalk Management database that contains the configuration information for the tracking profile you want to create.  
  
> [!NOTE]
>  The BizTalk Management database is also referred to as the BizTalk Configuration database.  
  
|Use this|To do this|  
|--------------|----------------|  
|**SQL Server**|Type the name of the computer running Microsoft SQL Server where the BizTalk Management database is located.<br /><br /> SQL connection strings can be specified in one of two ways:<br /><br /> -   You can specify just the server name and the Tracking Profile Editor (TPE) will connect to the default port.<br />-   You can specify a server name and port pair, ServerName, and port number. The TPE will connect to the SQL server using the specified port.|  
|**Database name**|Select the name of the BizTalk Management database from the drop-down list.|  
  
## See Also  
 [Tracking Profile Editor](../core/tracking-profile-editor.md)