---
title: "Adapter Handler Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.adapterhandler.properties.general"
ms.assetid: e67f67df-cf15-4c2f-bbb8-5a8d6ad8556d
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Handler Properties Dialog Box
Use the **Adapter Handler Properties** window to create and configure new adapter instances and to review and configure information for existing adapter instances. An adapter handler is a host that is responsible for executing the adapter and contains properties for a specific instance of an adapter.  
  
## General Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Adapter name**|Displays the name of the adapter with which the adapter handler is associated. Default adapters are named for the transport protocol they represent.|  
|**Properties**|Click to display the … **\<Adapter> Transport Properties** window, where you can configure adapter properties.|  
|**Host name**|From the drop-down list, select the name of the BizTalk Host with which the adapter handler is associated. When the adapter handler is created, BizTalk Server assigns the default host to run it. You can change that setting in this box.|  
|**Direction**|Displays the direction of communication for which the adapter is configured; specifically, whether the adapter supports a send port or a receive port.|  
|**Make this the default handler**|Select this check box to make the current adapter send handler the default. This check box is visible only for send handlers.|  
|**Description**|Type any text that is useful to you.|  
  
## See Also  
 [Using Adapters](../core/using-adapters.md)   
 [Adapter Groups and Group Adapters](../core/adapter-groups-and-group-adapters.md)