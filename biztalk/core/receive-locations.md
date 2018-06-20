---
title: "Receive Locations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive locations, properties"
  - "receive locations, about receive locations"
  - "receive locations"
  - "receive locations, receive location types"
ms.assetid: be5f7e5d-b63f-42f6-985e-895ba3912d34
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Locations
Creating a receive location involves specifying an address at which inbound messages arrive and the messaging pipeline that processes the message received at that address. Only administrators can create and enable receive locations.  
  
 An administrator uses the BizTalk Administration Console to create receive locations, bind receive locations to orchestrations, enable receive locations, disable receive locations, and set global properties for receive locations.  
  
 An administrator (using the BizTalk Administration Console) follows these steps to create a receive location:  
  
1.  Creates a receive location.  
  
2.  Associates the receive location with a host.  
  
3.  Binds the receive location to an orchestration.  
  
4.  Enables the receive location.  
  
5.  The receive location receives messages.  
  
> [!NOTE]
>  Changes to receive locations made by using Windows Management Instrumentation (WMI) affect how receive locations appear in the BizTalk Administration Console. For example, if an administrator uses WMI to create a new receive location, that receive location appears in the BizTalk Administration Console. Similarly, if an administrator deletes a receive location, the receive location disappears from the BizTalk Administration Console.  
> 
> [!IMPORTANT]
>  Each receive location must have a unique name. Two receive locations cannot have the same name in the same [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]deployment.  
> 
> [!IMPORTANT]
>  We recommend that you set strong access control lists (ACL) in the drop location for the receive locations. For example, you must set strong ACLs for the directory where the file receive location picks up messages, so that only authorized users can drop messages in this location.  
  
## Receive Location Types  
 There are two types of receive locations  
  
-   One-way. Used for applications that drop off a message and do not wait for a synchronous reply.  
  
-   Request-response. Used with applications that require a response to a message.  
  
## Receive Location Properties  
 Receive locations have global and adapter-specific properties. Administrators, using the BizTalk Administration Console, set global properties for all of the receive locations associated with a specific adapter.  
  
 Changes to receive location properties happen sequentially. If a solutions developer modifies a property value for a specific receive location, the new property value overrides the global property value for that receive location that the administrator set in the BizTalk Administration Console.  
  
## See Also  
 [Managing Receive Locations](../core/managing-receive-locations.md)   
 [Artifacts](../core/artifacts.md)