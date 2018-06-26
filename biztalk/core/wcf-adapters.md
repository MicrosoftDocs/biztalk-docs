---
title: "WCF Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e64cd189-8805-4209-bd06-971363f38585
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapters

## Overview
The BizTalk Adapters for Windows Communication Foundation (WCF) allow  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to communicate with WCF-based applications. The BizTalk WCF adapters include five physical adapters that represent the WCF predefined bindings—**BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, and **NetMsmqBinding**. The WCF adapters for the predefined bindings are provided to enable you to easily configure necessary information for most application requirements.  
  
 The BizTalk WCF adapters also include two adapters that enable you to freely configure WCF binding and behavior information for the receive location and send port.  

## Available WCF adapters
    
- **WCF-WSHttp adapter**. Provides the WS-* standards support over the HTTP transport. The WCF-WSHttp adapter implements the following specifications: WS-Transaction for the transactional interactions between external applications and the MessageBox database, and WS-Security for message security and authentication. The transport is HTTP or HTTPS, and message encoding is a Text or Message Transmission Optimization Mechanism (MTOM) encoding.  
  
- **WCF-BasicHttp adapter**. Communicates with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1. The transport is HTTP or HTTPS, and message encoding is a text encoding.  
  
- **WCF-NetTcp adapter**. Provides the WS-* standards support over the TCP transport. The WCF-NetTcp adapter provides efficient communication in a WCF-to-WCF environment. The adapter implements the following specifications: WS-Transaction for the transactional interactions between external applications and the MessageBox database, and WS-Security for message security and authentication. The transport is TCP, and message encoding is binary encoding.  
  
- **WCF-NetMsmq adapter**. Provides support for queuing by leveraging [!INCLUDE[btsCoName](../includes/btsconame-md.md)] Message Queuing (MSMQ) as a transport and enables support for loosely coupled applications, failure isolation, load leveling, and disconnected operations.  
  
- **WCF-NetNamedPipe adapter**. Provides secure optimization for on-machine cross-process communication. The WCF-NetNamedPipe adapter uses transport security for transfer security, named pipes for message delivery, and binary message encoding.  
  
- **WCF-Custom adapter**. Enables the use of WCF extensibility features. The adapter allows you to select and configure a WCF binding and the behavior information for the receive location and send port.  
  
- **WCF-CustomIsolated adapter**. Enables the use of WCF extensibility features over the HTTP transport. The adapter allows you to select and configure a WCF binding and the behavior information for the receive location running in an isolated host.  
  
  In addition, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides the BizTalk WCF Service Publishing Wizard and the BizTalk WCF Service Consuming Wizard. You can use the BizTalk WCF Service Publishing Wizard to create and publish BizTalk orchestrations as WCF services, and to publish schemas as WCF services. You can use the BizTalk WCF Service Consuming Wizard to generate [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] artifacts, such as orchestrations and types, to consume a WCF service based on the metadata document of the WCF service.  
  
  This section provides resources to help you configure and deploy the WCF adapters.  
  
## Next 
  
-   [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md)  
  
-   [Configuring the WCF Adapters](../core/configuring-the-wcf-adapters.md)  
  
-   [WCF-BasicHttp Adapter](../core/wcf-basichttp-adapter.md)  
  
-   [WCF-WSHttp Adapter](../core/wcf-wshttp-adapter.md)  
  
-   [WCF-NetTcp Adapter](../core/wcf-nettcp-adapter.md)  
  
-   [WCF-NetMsmq Adapter](../core/wcf-netmsmq-adapter.md)  
  
-   [WCF-NetNamedPipe Adapter](../core/wcf-netnamedpipe-adapter.md)  
  
-   [WCF-Custom Adapter](../core/wcf-custom-adapter.md)  
  
-   [WCF-CustomIsolated Adapter](../core/wcf-customisolated-adapter.md)  
  
## See Also  
 [Using WCF Services](../core/using-wcf-services.md)   