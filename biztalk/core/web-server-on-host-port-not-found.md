---
title: "Web server on host port not found | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c253fd5e-b815-4697-a06d-67af65a35589
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Web server on host port not found
## Details  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                         0                                          |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                                         0                                          |
|  Message Text   |                    Web server on host "{0}" port {1} not found                     |
  
## Explanation  
 This error indicates the World Wide Web (WWW) service is not running.  
  
## User Action  
 Use the following procedure to start the World Wide Web service.  
  
#### To start the World Wide Web service  
  
1.  Click **Start**, click **Control Panel**, double-click **Administrative Tools**, and double-click **Services.**  
  
2.  In the Name column, locate **World Wide Web Publishing**. Ensure that the status is **Started**.  
  
3.  Return to the **Administrative Tools** window. Double-click **Internet Information Services**.  
  
4.  Expand the folder area and locate the web site.  
  
5.  Ensure that the status is **Started**.