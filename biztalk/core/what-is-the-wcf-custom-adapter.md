---
title: "What Is the WCF-Custom Adapter? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF-Custom adapters, about WCF-Custom adapters"
ms.assetid: 7b2178dd-f737-4784-9bcb-e2b3979bfb0d
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the WCF-Custom Adapter?
The WCF-Custom adapter is used to enable the use of WCF extensibility components in BizTalk Server. The adapter enables complete flexibility of the WCF framework. It allows users to select and configure a WCF binding for the receive location and send port. It also allows users to set the endpoint behaviors and security settings.  
  
 The WCF-Custom adapter consists of two adapters—a receive adapter and a send adapter.  
  
 **WCF-Custom Receive Adapter**  
  
 You use the WCF-Custom receive adapter to receive WCF service requests through the bindings, service behavior, endpoint behavior, security mechanism, and the source of the inbound message body that you selected and configured in the transport properties dialog in the receive location. A receive location that uses the WCF-Custom receive adapter can be configured as one-way or request-response (two-way).  
  
 **WCF-Custom Send Adapter**  
  
 You use the WCF-Custom send adapter to call a WCF service through the typeless contract with the bindings, service behavior, endpoint behavior, security mechanism, and the source of the outbound message body that you selected and configured.  
  
 For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).  
  
## See Also  
 [Configuring the WCF-Custom Adapter](../core/configuring-the-wcf-custom-adapter.md)   
 [WCF Adapters](../core/wcf-adapters.md)