---
title: "Adapter Programming Administration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38563b3c-6d52-4e4e-ac6e-74f46ce22c6a
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Programming Administration
An adapter is a special type of configuration store application: that is, an adapter is a component that shares a namespace with other Single Sign-On and configuration store applications. Therefore, you can access information about an adapter using ISSOConfigStore. But unlike a configuration store application, you do not perform administrative functions on an adapter with the ISSOAdmin interface. Instead, you administer an adapter through ISSOPSAdmin. The reason for a specialized adapter administration interface is so that the system can coordinate other activities with the configuration store.  
  
## See Also  
 [Adapter Programming Configuration](../core/adapter-programming-configuration.md)   
 [Adapter Groups and Group Adapters](../core/adapter-groups-and-group-adapters.md)   
 [Password Sync Adapters](../core/password-sync-adapters.md)