---
description: "Learn more about: Understand WCF security on the adapter created with the WCF LOB Adapter SDK"
title: "Understand WCF security on the adapter created with the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1ee402b-ffda-42c1-8d85-d7cbe073a307
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Understand WCF security on the adapter created with the WCF LOB Adapter SDK
The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] extends the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel architecture and relies on the messaging infrastructure and the API that it provides.  A WCF LOB adapter needs to establish a connection to target systems, and hence it is necessary to configure the adapter with authentication and other security information required to make the target system connections.  
  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] is a distributed programming platform based on SOAP messages that can travel through many different nodes, SOAP intermediaries, firewalls, and potentially the Internet en-route from the line-of-business system to the adapter and on to the client. This could present a number of different security threats to your adapter and deployment scenario.  
  
 Security plays a major part in any enterprise architecture solution. You can leverage the confidentiality, integrity, authentication, and authorization features provided in the WCF security model to help secure the adapter from security threats. You must also consider the transport and message-level security between the adapter and the target system to protect the communication between these two entities. Even though WCF provides a rich set of WS-* specifications, implementation of these advanced security standards in your adapter will depend on the capabilities provided by the line-of-business system.  
  
 For more information about [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] security including an overview, concepts, common scenarios, and best practices, see [Windows Communication Foundation Security](/dotnet/framework/wcf/feature-details/security).
  
## See Also  
 [Plan and design an adapter using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)