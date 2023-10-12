---
description: "Learn more about: Adapter Programming Administration"
title: "Adapter Programming Administration"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Adapter Programming Administration
An adapter is a special type of configuration store application: that is, an adapter is a component that shares a namespace with other Single Sign-On and configuration store applications. Therefore, you can access information about an adapter using ISSOConfigStore. But unlike a configuration store application, you do not perform administrative functions on an adapter with the ISSOAdmin interface. Instead, you administer an adapter through ISSOPSAdmin. The reason for a specialized adapter administration interface is so that the system can coordinate other activities with the configuration store.  
  
## See Also  
 [Adapter Programming Configuration](../esso/adapter-programming-configuration.md)   
 [Adapter Groups and Group Adapters](../esso/adapter-groups-and-group-adapters.md)   
 [Password Sync Adapters](../esso/password-sync-adapters.md)
