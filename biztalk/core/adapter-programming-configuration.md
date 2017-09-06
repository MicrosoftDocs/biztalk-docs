---
title: "Adapter Programming Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e5fef6c-6928-42e7-9a1f-42b5bd769937
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Programming Configuration
Every type of password sync adapter has different configuration requirements, depending on what non-Windows system you design the adapter for. Like affiliate applications, you can use the Enterprise Single Sign-On configuration store to store configuration properties centrally and more securely.  
  
 As with other configuration store applications, an administrator can use the Enterprise Single Sign-On management user interface to locate and read an XML file that describes the configuration properties for your adapter. The management tools use the XML file to render a property page to gather the required property values, for the specified adapter. You can also use ISSOConfigStore to load and read XML name/value combinations to and from the configuration store, or you can use the SSOPS tool.  
  
 You can also use the Enterprise Single Sign-On administration tools to enable and disable an adapter. On initial creation, an adapter is disabled.  
  
## See Also  
 [Password Sync Adapters](../core/password-sync-adapters.md)