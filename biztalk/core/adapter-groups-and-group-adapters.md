---
title: "Adapter Groups and Group Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e0a9423-99dd-4474-afa1-fd8e1d074cd1
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Groups and Group Adapters
An *adapter group* is an administration mechanism that you can use to collect and organize a set of adapters. In contrast, a *group adapter* is a component that services all adapters in an adapter group. For example, you might write a set of adapters that all use the same COM component to transmit password synchronizations over TCP/IP. Your set of adapters is called the adapter group, whereas the component that services them all is called a group adapter. Adapter groups are described in the configuration store. You can retrieve information and updates on an adapter group by using `ISSOPSAdapter.ReceiveNotification`.  
  
 A group adapter has the same name as the adapter group. Other than the naming restriction, a group adapter is otherwise identical to a normal adapter. For example, a group adapter can have independent access groups and configuration properties, as described by its configuration file. A group adapter is most likely on the same computer as any adapters in the adapter group. However, this is not currently enforced. Likewise, all adapters in the same adapter group can be expected to be on the same computer.  
  
 By using `ISSOPSAdapter.InitializeAdapter`, you can access and initialize a group adapter during startup. When you initialize a group adapter, the system informs the group adapter of all adapters in the adapter group on the current system. In addition, the system sends notifications to the group adapter any time an adapter is added, deleted, enabled, or disabled in the adapter group. However, the group adapter does not receive any password change notifications.  
  
 Adapter groups and group adapters are optional using the Administration tool.  
  
## See Also  
 [Password Sync Adapters](../core/password-sync-adapters.md)