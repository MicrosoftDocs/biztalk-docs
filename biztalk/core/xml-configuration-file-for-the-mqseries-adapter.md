---
description: "Learn more about: XML Configuration File for the MQSeries Adapter"
title: "XML Configuration File for the MQSeries Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MQSeries adapters, mqsconfigwiz"
  - "configuring [MQSeries adapters], silent configuration"
  - "MQSeries adapters, silent configuration"
  - "configuring [MQSeries adapters], mqsconfigwiz"
  - "mqsconfigwiz [MQSeries adapters]"
ms.assetid: 5f19e55c-0f2c-46d7-bb5d-1eb147c296b3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XML Configuration File for the MQSeries Adapter
The XML configuration file read by **mqsconfigwiz** contains the same information a user enters when using the Windows version of the wizard. This information includes the application identity and the user ID and password if required, the role name, and a list of users who are part of that role.  
  
 An example of the file might appear as follows:  
  
```  
<MQSeriesConfig>  
    <AppIdentity>thisuser</AppIdentity>  
    <userid>domain\username</userid>  
    <password>Bippity.Boppity</password>  
    <rolename>CreatorOwner</rolename>  
    <userlist>  
        <username>domain\user1</username>  
        <username>domain\user2</username>  
    </userlist>  
</MQSeriesConfig>  
```  
  
 You can use **thisuser**, **InteractiveUser**, **LocalService**, or **NetworkService** as values for **AppIdentity**. Use the **userid** and **password** elements only with **thisuser**.  
  
## See Also  
 [Silent Configuration of the MQSeries Adapter](../core/silent-configuration-of-the-mqseries-adapter.md)
