---
title: "TIBCO Rendezvous Events and Receive Locations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive locations, life cycle"
ms.assetid: 3576af82-4723-4efc-961e-40b1150cf13d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TIBCO Rendezvous Events and Receive Locations
Any TIBCO Rendezvous system can send messages to their subject name of choice. The concept of *event* is the generation of messages by other TIBCO Rendezvous programs.  
  
 The following steps describe the life cycle of a receive location:  
  
1.  Receive location is created.  
  
2.  Receive location is associated with a host.  
  
3.  Receive location is bound to an orchestration.  
  
4.  Receive location is enabled.  
  
5.  Receive location receives messages.  
  
> [!IMPORTANT]
>  Each receive location must have a unique name. Two receive locations cannot have the same name in the same [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.  
  
> [!IMPORTANT]
>  It is recommended that you set strong access control lists (ACL) in the receive locations drop locations. For example, you must set strong ACLs for the directory where the file receive location picks up messages, so that only authorized users can drop messages in this location.  
  
## See Also  
 [Creating TIBCO Rendezvous Receive Handlers](../core/creating-tibco-rendezvous-receive-handlers.md)