---
title: "Adapter Programming Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9292d25-6a4e-49c9-a3ad-a194680b324f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Adapter Programming Configuration
Every type of password sync adapter has different configuration requirements, depending on what non-Windows system you design the adapter for. Like affiliate applications, you can use the Enterprise Single Sign-On configuration store to store configuration properties centrally and more securely.  
  
 As with other configuration store applications, an administrator can use the Enterprise Single Sign-On management user interface to locate and read an XML file that describes the configuration properties for your adapter. The management tools use the XML file to render a property page to gather the required property values, for the specified adapter. You can also use ISSOConfigStore to load and read XML name/value combinations to and from the configuration store, or you can use the SSOPS tool.  
  
 You can also use the Enterprise Single Sign-On administration tools to enable and disable an adapter. On initial creation, an adapter is disabled.  
  
## See Also  
 [Password Sync Adapters](../esso/password-sync-adapters.md)