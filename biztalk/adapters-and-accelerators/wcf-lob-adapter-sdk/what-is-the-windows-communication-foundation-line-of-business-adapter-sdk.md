---
title: "What Is the Windows Communication Foundation Line of Business Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc690e8f-fd37-44b5-a277-89952e631ae6
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the Windows Communication Foundation Line of Business Adapter SDK
Overview of the features and components in the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. This topic also describes the key concepts, including metadata, connection management, and terms to know, such as binding and channel.

## Features overview
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] was designed to meet the needs of developers building adapters that expose the data and operations of line-of-business systems. Some of the features provided by the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] include:  
  
- A consistent mechanism for exposing transport and data protocols
  
- Exposure of the adapter as a WCF binding
  
- Extensibility through the WCF channel architecture
  
- [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]
  
- Common metadata search and browse user interface using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]
  
- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] design-time integration using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]
  
  Because the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is an extension to WCF, it also provides the following features:  
  
- A unification of existing .NET Framework communication technologies
  
- Support for cross-vendor interoperability, including reliability, security, and transactions
  
- An explicit service orientation
  
## Components overview
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides a consistent and repeatable experience for both the adapter developer and the adapter consumer through a set of run-time and design-time components, a .NET object model, and support components including:  
  

|                                        Component                                        |                                                                                                       Description                                                                                                        |
|-----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]        |         Provides step-by-step guidance in the creation of [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] projects within [!INCLUDE[btsVStudioNet](../../includes/btsvstudionet-md.md)].         |
|            [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]            |                                                   Provides step-by-step guidance in creating a Web project to host an adapter in Internet Information Services (IIS).                                                    |
| [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] run-time system |                          Supports the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] by extending the WCF channel architecture and providing other run-time services.                           |
|  [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] object model   |                  A collection of classes, types, and interfaces that support common adapter tasks such as metadata normalization, caching, connection management and pooling, and messaging inspection.                  |
|     [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]     |                               Gives custom .NET applications the ability to consume adapters developed using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].                                |
|    [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]    | Gives [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] the ability to consume adapters developed using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. |

## SDK fundamentals  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] consists of a runtime, a collection of APIs, and design-time tools for creating adapters that expose data and operations from line-of-business systems. Adapters manage messages between the adapter consumer and the line-of-business system and can consist of metadata, data, or other information.  

### Metadata  
 One of the distinguishing characteristics of an adapter written with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and one implemented using the Windows Communication Foundation (WCF) Service Model object model is metadata. Metadata describes the data, operations, properties, and other dynamic characteristics of a system and is used by the adapter consumer to discover, consume, and interact with a target system.  

 A typical WCF service programming lifecycle includes a WCF service developer creating and hosting a service. A WCF service endpoint consists of an address, a binding, and a contract, also known as the "A, B, and C's" of WCF.  The address is the location of the service, while the binding specifies the protocols and the transports used to communicate with the service.  A WCF service developer defines a contract using the WCF System.ServiceModel object model, provides its implementation in the form of a WCF service, and hosts it using ServiceHost. The SvcUtil.exe and/or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] can be used to build the client corresponding to the published service's metadata. Once the service is up and running, the design-time tool can be run against the service endpoint address to generate the WCF proxy in a preferred language and an app.config file for the client implementation that corresponds with the details of the WCF service.  

 A WCF LOB adapter developer, on the other hand, implements the metadata object model provided in the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] to define the operations and types supported by the adapter. Since the outbound adapter is a WCF custom binding, it is hosted in-proc within the consumer application.  Once the adapter is installed on a computer, [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] can be used to browse and search metadata, and to consequently generate the WCF proxy in a preferred language along with an app.config file that contains the adapter configuration details. The contract is created and generated on-demand by the WCF LOB adapter by querying the live metadata available in the line-of-business system.  

 For example, a line-of-business system may adjudicate different types of health care claims and may contain a growing collection of unique operations, data types, business rules, and reports created by users of the system. If this information is exposed as a static contract, it has to be modified as new business objects are added to the system or simply not provide access to new business objects. However, if information about the dynamic business object within the claims adjudication system is browsable (and searchable), new objects such as a new validation rule for institutional claims or a new report are exposed and can be consumed.  

### Connection Management  
 Before information can be exchanged with the line-of-business system, the adapter must establish a connection. A connection links the adapter (the consumer) to the line-of-business system (the provider) and controls the connection lifecycle including opening, closing, aborting, and verifying connection validity. Based on the requirements of the line-of-business system, the connection may require one or more credentials and connection parameters such as server name, default directory, or port number.  

 Connection lifetime is managed by a connection pool. When a new connection is requested by the adapter, the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides an existing connection if one is available; otherwise, a new connection is created and placed into the pool and then provided to the adapter. When the adapter is done with the connection, it is placed back into the pool. Connections that are idle beyond a certain threshold are closed and removed from the pool.  

### Windows Communication Foundation  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is an extension of the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], a unified programming model for building service-oriented applications with managed code. Adapters written using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] are surfaced as [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] bindings that can be consumed by any WCF-capable application.  

## Important terms  

|           |                                                                                                                                                                                                                                                         |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  binding  | Defines how an adapter communicates. Bindings are created by the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and define the transport, encoding, and other details. There may be one or more binding elements in a binding. |
|  channel  |                                                          The implementation of a binding element. Collections of channels for a binding stack on top of each other to create a channel stack.                                                           |
|  message  |                                                                              A self-contained unit of data that may consist of several parts including a body and headers.                                                                              |
| metadata  |                                                                   Describes the characteristics of the line-of-business system including the operations and data that are available.                                                                    |
| operation |                             The functions and methods exposed by a line-of-business system. They operate on data and perform useful activities such as adjudicating claims, creating an order, or querying for sales data.                              |
   
## See Also  
 [BizTalk Server and the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/using-biztalk-server-and-the-wcf-lob-adapter-sdk.md)   
   [WCF LOB Adapter SDK Tutorials](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)