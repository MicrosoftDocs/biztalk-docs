---
title: "ESB Resolver and Adapter Provider Framework | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c82c2247-1f0a-48bd-98c2-9c816f4d68d7
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ESB Resolver and Adapter Provider Framework
The Resolver and Adapter Provider Framework provides a comprehensive, pluggable architecture for dynamically resolving endpoint information and BizTalk Server map types. It uses extensible components, which allow developers to change the behavior to suit their own requirements and extend the mechanism to support alternative resolution and routing methods.  
  
 The Resolver and Adapter Provider Framework provides support Universal Description, Discovery, and Integration (UDDI), Business Rule Engine (BRE), and XML Path Language (XPath). It also exposes developer interfaces (**IResolveProvider** and **IAdapterProvider**) to allow creation of custom resolver and adapter components. The following are the three main components of the Resolver and Adapter Provider Framework:  
  
- **Resolvers.** These are defined by a schema, connection string, and through the implementation of the **IResolveProvider** interface in a .NET Framework assembly. These are loaded and cached at run time and support a range of resolution types and connection strings.  
  
- **Adapter providers.** These are defined through the implementation of the **IAdapterProvider** interface within a .NET Framework assembly. These are registered by their BizTalk Server transport type, which set the endpoint information provided by a resolver on the appropriate BizTalk Server adapter.  
  
- **Itinerary pipeline components.** These parse resolution instructions from connection strings or from the ESB Itinerary SOAP headers, and they provide endpoint resolution or transformation execution capabilities using the Resolver and Adapter Provider Framework. The components can dynamically set the BizTalk Server endpoint properties or execute a BizTalk Server map transformation based on resolution instructions from the connection string or from the ESB Itinerary SOAP headers. These components are responsible for managing, updating, and persisting the itinerary across process and service boundaries. The optional Disassembler component provides native BizTalk Server parsing of the message and implements the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] feature of routing to multiple endpoints without the need for an orchestration service.  
  
  For more information about dynamic resolution and dynamic routing, see [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md) and [Using Dynamic Transformation](../esb-toolkit/using-dynamic-transformation.md). For information about the Resolution and Adapter Provider Framework, see [Modifying and Extending the BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md).