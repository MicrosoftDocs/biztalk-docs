---
title: "How to Configure a Password Sync Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0effdc9b-4aee-4674-90c5-03dfd7cc4cd6
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a Password Sync Adapter
After you have finished creating your password sync adapter, you must load your adapter on to a system. Additionally, you must inform Enterprise Single Sign-On (ENTSSO) and the configuration store that your application is a password sync adapter. You must register with the configuration store for security purposes: your adapter will request updates to passwords and other credentials. Therefore, ENTSSO must know that a given adapter is allowed to ask for such permissions.  
  
### To configure a password sync adapter  
  
1.  Create your adapter with the configuration store using the ssops tool.  
  
     Using ssops, you load an XML configuration file into the configuration database that describes your application to Enterprise Single Sign-On.  
  
2.  After you create the adapter with the config database, you can modify the adapter information with `ISSOPSAdmin.SetAdapterProperties`.  
  
     While the two methods are similar, `SetAdapterProperties` sends a message to the adapter when the configuration information changes.  
  
3.  To delete an adapter, use ISSOAdmin.DeleteApplication.  
  
## See Also  
 [Synchronizing Passwords](../core/synchronizing-passwords.md)