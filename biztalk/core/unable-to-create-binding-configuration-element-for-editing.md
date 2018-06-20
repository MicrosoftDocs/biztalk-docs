---
title: "Unable to create binding configuration element for editing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71853662-5a4a-417e-8160-c93dbcbea336
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unable to create binding configuration element for editing
## Details  
  
|                 |                                                                                                                                      |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                          |
| Product Version |                                      [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                      |
|    Event ID     |                                                                  0                                                                   |
|  Event Source   |                                                                  0                                                                   |
|    Component    |                                                                  0                                                                   |
|  Symbolic Name  |                                                                  0                                                                   |
|  Message Text   | Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties. |
  
## Explanation  
 There was an error loading a binding element for display in the user interface. This error often occurs with custom binding. The binding element is probably missing in the configuration file and is therefore not available on the drop-down list for binding.  
  
## User Action  
 Check the values of the **BindingType** and **BindingConfiguration** properties.  
  
 For further information on creating binding configuration elements, see the following resource:  
  
-   [Configuring the WCF-NetMsmq Adapter](../core/configuring-the-wcf-netmsmq-adapter.md)