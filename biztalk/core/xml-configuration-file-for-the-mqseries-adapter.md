---
description: "Learn more about: XML Configuration File for the MQSeries Adapter"
title: "XML Configuration File for the MQSeries Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
