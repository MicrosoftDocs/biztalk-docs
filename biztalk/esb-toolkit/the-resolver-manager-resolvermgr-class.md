---
title: "The Resolver Manager (ResolverMgr) Class | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 89fa551d-0aca-4777-adbc-2bc46ab8664a
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Resolver Manager (ResolverMgr) Class
The Transform and Routing messaging services use the **ResolverMgr** class to perform resolution. The ESB dynamic transformation and dynamic delivery agents also use the **ResolverManager** class to perform just-in-time (JIT) resolution.  
  
 The ESB Core installer installs and registers the **Microsoft.Practices.ESB.Resolver.dll** assembly with the **ResolverMgr** class in the global assembly cache.  
  
 You can use this class in your own code where you need to perform dynamic resolution of endpoints or maps. You can also extend this class to use a custom resolution method. However, keep in mind that the class already supports a resolution mechanism that can use any custom resolver assembly, which should accommodate any alternative resolution algorithm you may require.  
  
 The following code example shows how to use the **ResolverMgr** class to resolve an endpoint.  
  
```csharp  
// Move to retrieve the first resolver.  
resolvers = itineraryStep.ResolverCollection;  
resolver = resolvers.Current;  
  
// Pass the resolver configuration to the Resolver Manager for resolution.  
resolverDictionary = Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage, resolver);  
  
// Set transport properties.  
transportLocation = resolverDictionary.Item("Resolver.TransportLocation");  
transportType = resolverDictionary.Item("Resolver.TransportType");  
```  
  
 Usually, your resolver connection string specifies the property values for at least one resolution method, such as a rules policy, custom assembly, XPath statement, or Universal Description, Discovery, and Integration (UDDI) label and server name. Finally, it returns a dictionary object with a collection of resolver facts, which can be easily populated with custom facts from a concrete resolver.  
  
 For more information about how the ESB resolution mechanism works, see [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md).