---
title: "Create a connection to the Siebel system | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connecting, to the Siebel system"
ms.assetid: 5810eeb1-6e26-4620-a731-fb352eebea2e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create a connection to the Siebel system
The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding. As such, it enables communication to a Siebel system through a WCF endpoint address. In WCF the endpoint address identifies the network location of a service and is typically expressed as a Uniform Resource Identifier (URI). The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses to establish a connection to the Siebel system. You must specify a connection URI when you:  
  
- Create a channel factory or a channel listener using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model, or create a WCF client or service host using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model.  
  
- Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
- Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class, or WCF service interface for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model solution.  
  
- Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] for a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
- Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class, or WCF service interface for a WCF service model solution.  
  
  The topics in this section describe how to establish a connection between the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] and the Siebel system by providing you with:  
  
- Information about the connection properties and the structure of the Siebel connection URI.  
  
- Links to topics that show how to establish a connection by using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  

  
## See Also  
[Develop your Siebel applications](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)