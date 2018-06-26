---
title: "Using Dynamic Transformation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1e4aac7-242a-41b6-8df4-4881371f44d1
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Dynamic Transformation
## Overview  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports three mechanisms for dynamic transformation:  
  
- A dynamic transformation agent implemented as an orchestration  
  
- A dynamic transformation Web service included with the core Web services  
  
- Transformations executed by ESB pipeline components  
  
  This section focuses on the transformation agent implemented as an orchestration. For information about the transformation Web service, see [Using the BizTalk ESB Toolkit Web Services](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md). For information about the ESB Dispatcher pipeline components, see [Using the Pipeline Support Components](../esb-toolkit/using-the-pipeline-support-components.md).  
  
## How It Works  
 The transformation delivery agent is an orchestration that subscribes to messages where the **Name** attribute of the current **ServiceInstance** element in the itinerary is **Microsoft.Practices.ESB.Services.Transform**. The agent performs the following sequence of operations:  
  
1.  It receives an un-typed message (System.Xml.XmlDocument).  
  
2.  If the name of the map is available as a static value in the itinerary, the agent attempts to resolve the name of the map using the resolver manager.  
  
3.  It applies the appropriate map to the inbound source message.  
  
4.  It publishes the map output to the BizTalk Message Box database.  
  
## How to Configure Dynamic Transformation  
 For more information about how to configure Dynamic Transformation using Itinerary Designer, see [Creating Itineraries Using Itinerary Designer](../esb-toolkit/creating-itineraries-using-itinerary-designer.md).  
  
## Dynamic Transformation Errors  
 The dynamic transformation mechanism will create and publish an ESB fault message in the following cases:  
  
- The resolver component cannot determine which map to apply.  
  
- The specified map is not available (for example, you specified an incorrect map type or a map not yet deployed in BizTalk Server 2009).  
  
- A failure occurs during mapping (for example, the source document is not of the correct source type or the map references a custom function in an external assembly is not deployed to BizTalk).  
  
- An exception occurs during just-in-time (JIT) resolution of the map type.  
  
- No subscriber exists for the output message.  
  
- Any system exception occurs.  
  
  It is the developer's responsibility to provide the context information used to populate the exception messages and create handlers to react to the exception. Some of the data is automatically available, and a generic handler will pick up the exception message if no target handler is specified or available. For more information about handling dynamic transformation exceptions, see [Using ESB Exception Management](../esb-toolkit/using-esb-exception-management.md).