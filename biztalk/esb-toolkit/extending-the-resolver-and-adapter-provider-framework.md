---
description: "Learn more about: Extending the Resolver and Adapter Provider Framework"
title: "Extending the Resolver and Adapter Provider Framework | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4d5e6f2-b3bc-46e2-b8f7-d7e271d4a8c0
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Extending the Resolver and Adapter Provider Framework
The Resolver and Adapter Provider Framework provides support for endpoint and transformation resolution and routing, and it can also provide custom metadata for services. The framework can dynamically resolve endpoints and set outbound adapter properties. After a resolver component resolves an endpoint (for example, using Universal Description, Discovery, and Integration [UDDI] to look up an outbound URL), an adapter provider component sets specific properties of registered Microsoft BizTalk Server adapters.  
  
 There are three main areas where you can extend the Resolver and Adapter Provider Framework:  
  
-   [Creating a Custom Resolver](../esb-toolkit/creating-a-custom-resolver.md)  
  
-   [Creating a Custom Resolver with a Unity Container](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md)  
  
-   [Creating a Custom Adapter Provider](../esb-toolkit/creating-a-custom-adapter-provider.md)
