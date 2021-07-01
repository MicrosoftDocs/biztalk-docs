---
description: "Learn more about: View the supported message exchange patterns in the WCF LOB Adapter SDK"
title: "View the supported message exchange patterns in the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6662f17-b4f8-45fe-a22f-5d027dc9f2ff
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# View the supported message exchange patterns in the WCF LOB Adapter SDK
The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] supports several of the messaging patterns supported by the underlying [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] including request-reply, and one-way communication. Different transports support different messaging patterns, and thus affect the types of interactions that they support.  
  
 The patterns listed in the following table are handled by the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].  
  
|Pattern|Description|  
|-------------|-----------------|  
|One-way inbound|Inbound messages are received from the line-of-business system but no response is expected from the adapter.|  
|Request-response inbound|Inbound messages are received from the line-of-business system which expects an appropriate response from the adapter.|  
|One-way outbound|Outbound messages are sent to the line-of-business system but no response is expected from the adapter.|  
|Request-response outbound|Outbound messages are sent to the line-of-business system with a response expected from the adapter.|  
|Sessionful inbound|Inbound messages are received from the line-of-business system within a unique session. No response is expected by the line-of-business system from the adapter.|  
|Sessionful outbound|Outbound messages are sent to the line-of-business system within a unique session. No response is expected from the line-of-business system by the adapter.|  
  
 Your choice of message pattern will be guided by the functionality of the target application.  
  
## Planning for Sessions  
 A messaging pattern may use a session when it wants to ensure that all messages exchanged between the adapter and the line-of-business system must be part of the same conversation. Typically sessions are used when delivery guarantee is needed, but they can also be used to support other requirements that an adapter developer may have for message exchange.  
  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] relies on the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] for session support. For more information about sessions, see [Sessions, Instancing, and Concurrency](/dotnet/framework/wcf/feature-details/sessions-instancing-and-concurrency). 
  
## See Also  
 [Plan and design an adapter using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)