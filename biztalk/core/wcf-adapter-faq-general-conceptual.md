---
title: "WCF Adapter FAQ: General Conceptual | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bbeac135-3ba8-4b0b-a8ca-4eb5eb3d3ca3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapter FAQ: General Conceptual
Below are some frequently asked general and conceptual questions about Windows® Communication Foundation (WCF) adapters.  
  
## What is a WCF adapter?  
 A BizTalk adapter is a key part of the way Microsoft® BizTalk® Server communicates with the outside world. A WCF adapter is a component that manages the communication process between a BizTalk application and its need to send messages to, and receive messages from, a WCF endpoint. With the BizTalk Server, WCF adapters are exposed as WCF bindings. This means that any WCF application that can use a WCF binding can communicate with the WCF adapters directly, without needing BizTalk Server to intervene. However, using the WCF adapters through BizTalk Server gives you many of the application infrastructure benefits that BizTalk Server provides. The focus of these FAQs is primarily using the WCF adapters from within the BizTalk Server environment.  
  
 A WCF adapter allows BizTalk Server to use the WCF bindings to send and receive WCF messages. A WCF client application can send a WCF message to a BizTalk receive location, where the message is received by a WCF receive adapter. The adapter takes the WCF message and converts it to a BizTalk message. How the conversion takes place depends upon certain adapter configuration settings which are configured using the BizTalk Server Administration console. The adapter submits the BizTalk message to the internal BizTalk MessageBox database. Correspondingly, a BizTalk send port using a WCF adapter can subscribe to this message type, obtain the BizTalk message, convert it to a WCF message, and transmit the WCF message to a WCF service endpoint using one of the supported WCF protocols.  
  
 Using the WCF adapters from within BizTalk Server abstracts the hidden complexities of a BizTalk-WCF application solution, such as the choice and implementation of communication protocols, security issues, and transactional operations.  
  
## What are the WCF adapter bindings?  
 WCF bindings fall into one of two categories:  
  
- **Custom Bindings:** For increased binding flexibility, the special custom binding exists. This covers communication situations that require deviations from the standard bindings. The WCF-Custom and WCF-CustomIsolated adapters allow development of extensive binding customizations. This is done by allowing the composition of existing binding elements (the BindingElement class) and the application of behaviors (the Behavior class).  
  
- **Standard bindings:** Microsoft’s goal is to develop adapters focused on the most common communication scenarios. Using standard bindings simplifies the developer’s experience by hiding many details of the communication protocols. The set of WCF adapters in BizTalk Server reflects the set of bindings available in the .NET Framework 4.0 WCF libraries. Standard bindings were introduced to the .NET WCF libraries to make typical binding patterns easier to use. They cover the most commonly used communication scenarios and include:  
  
  -   WCF-WsHttp  
  
  -   WCF-BasicHttp  
  
  -   WCF-NetTcp  
  
  -   WCF-NetMsmg  
  
  -   WCF-NetNamedPipe  
  
  BizTalk Server R2 ships with the following WCF adapters:  
  
1.  **WCF-WSHttp adapter:**  Provides the WS-* standards support over the HTTP transport. The WCF-WSHttp adapter implements the following specifications: WS-Transaction for the transactional interactions between external applications and the MessageBox database, and WS-Security for message security and authentication. The transport is HTTP or HTTPS, and message encoding is a text or Message Transmission Optimization Mechanism (MTOM) encoding.  
  
2.  **WCF-BasicHttp adapter:** Communicates with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1. The transport is HTTP or HTTPS, and message encoding is a text encoding.  
  
3.  **WCF-NetTcp adapter:** Provides the WS-* standards support over the TCP transport. The WCF-NetTcp adapter provides efficient communication and implements the following specifications: WS-Transaction for the transactional interactions between external applications and the MessageBox database, and WS-Security for message security and authentication. The transport is TCP, and message encoding is binary encoding.  
  
4.  **WCF-NetMsmq adapter:** Provides support for queuing by leveraging Message Queuing (also known as MSMQ) as a transport and enables support for loosely coupled applications, failure isolation, load-leveling, and disconnected operations.  
  
5.  **WCF-NetNamedPipe adapter:** Provides secure optimization for on-machine cross-process communication. The WCF-NetNamedPipe adapter uses transport security for transfer security, named pipes for message delivery, and binary message encoding.  
  
     Each of the five adapters just mentioned correspond to one WCF binding in a 1:1 relationship. The structure of the two custom adapters we are about to discuss slightly breaks with the WCF model in that there are actually two distinct custom adapters that correspond to the single WCF CustomBinding.  
  
6.  **WCF-Custom adapter:** Enables the use of WCF extensibility features. The adapter allows you to select and configure a WCF binding and the behavior information for a receive location or a send port hosted in the BizTalk Server process.  
  
7.  **WCF-CustomIsolated adapter:** Enables the use of WCF extensibility features over the HTTP transport. The adapter allows you to select and configure a WCF binding and the behavior information for a receive location running in the isolated host of Internet Information Services (IIS).  
  
## What is the difference between the WCF-xxx adapter and the WCF-xxx binding?  
 Each of the WCF adapters corresponds to one of the built-in WCF bindings. At a higher level, these terms are used almost interchangeably when saying that the WCF-xxx adapter uses the WCF-xxx binding. For example, the WCF-BasicHttp adapter uses the WCF BasicHttpBinding class. A WCF binding is part of the definition of a WCF Endpoint. This is referred to in the “ABC” of a WCF endpoint, where these letters stand for Address, Binding and Contract.  
  
 A binding is made up of a collection of binding elements. Each element describes some aspect of how the endpoint communicates with clients. A binding must include:  
  
- At least one transport binding element.  
  
- At least one message-encoding binding element (which the transport binding element can provide by default).  
  
- Any number of other protocol binding elements.  
  
  The process that builds a runtime environment out of this description allows each binding element to contribute code to that environment. It is generally required for a client to match the same binding types and adapter that the called WCF Service supports. At the WCF level, a binding can be defined declaratively in a configuration file or explicitly through code. A WCF adapter facilitates communication using a specific WCF binding, and thus the terms “adapter” and “binding” tend to become almost identical in their usage.  
  
## When using the WCF adapters, how do you decide which WCF binding to use?  
 You can make this decision based upon the messaging pattern, external constraints, and performance, in that order.  
  
1.  **Messaging pattern:** The pattern of communication is how the communication occurs based on the flow of the message. For example, the message may be one-way (request) or two-way (request-response), it may be transacted, it may be queued, and so on.  
  
    -   If it is queued, you need to use the WCF-NetMsmq adapter, which supports one-way queued transacted communication.  
  
    -   If the pattern is a two-way request-response and flows between two computers, you would use HTTP (if you are concerned about being as flexible as possible), or WCF-NetTcp (if you are concerned about performance).  
  
    -   If the message remains on a single computer and flows simply between processes, you can use the WCF-NetNamedPipe binding.  
  
2.  **External constraints:** There may be issues that dictate you use a specific binding. For instance, suppose the external system requires SOAP Web Services version 1.2 and Addressing 1.0. In this case, the best binding choice is WSHttpBinding using the WCF-WsHttp adapter. In all likelihood, the external system would also have requirements around the particular security mode to configure. If the external system required Soap Web Services 1.1 you would use the WCF-BasicHttp adapter for the HTTP binding.  
  
3.  **Performance:** How fast the call is made may be a deciding factor in which binding you choose to use in your application:  
  
    -   If the WCF service is on the same computer as BizTalk Server, using the WCF-NetNamedPipe adapter is the best performance choice.  
  
    -   If the WCF service is on your local network, WCF-NetTcp yields the best performance.  
  
    -   If performance is not a major concern and the call is going across the Internet, either of the HTTP-based adapters (WCF-WsHttp or WCF-BasicHttp) is the right adapter.  
  
         Whether you are using any advanced HTTP functionality (WCF-WsHttp) or just basic functionality (WCF-BasicHttp) will dictate which HTTP-based adapter is the best choice to use.  
  
## When do you use one of the two custom WCF adapters?  
 There are two custom WCF adapters that ship with BizTalk Server. The reason there are two custom adapters is because BizTalk Server requires that the hosting of a particular adapter type needs to be part of its registration with the system. Although there is only one CustomBinding type in the WCF  Framework, there are two custom adapters in BizTalk Server to accommodate this limitation in the pre-existing BizTalk adapter model. In reality, these adapters are really the only adapters you ever need because they allow complete control over the WCF channel stack configuration.  
  
 The only drawback to custom adapters is that they also require you to be very knowledgeable about WCF configuration and the various extensibility techniques.  Simplifying configuration is why Microsoft provides adapters for standard WCF bindings. The standard bindings are predefined to cover most of the common use cases and to make sending and receiving messages through BizTalk Server as simple as possible. The need to use one of these custom adapters typically occurs only when the standard bindings fail to completely or precisely meet the requirements for your send port or receive location. For example, there may be an application using a proprietary compression scheme for its messages. To support this, a custom binding element will have to be written. Using one of the two standard custom adapters allows configuration of this custom binding to handle the transmission requirement. Thus, a custom adapter allows a higher level of control over the configuration of the bindings for that communication process through the channel stack.  
  
 The primary difference between the Custom and Custom Isolated adapters is one of hosting, and hosting only impacts the receive side of BizTalk Server. The WCF-CustomIsolated adapter is used with a receive location only and not with a send port. The term “Isolated” is a BizTalk phrase that refers to being hosted outside of the BizTalk Server BtsNtSvc.exe process. Therefore, the WCF-CustomIsolated adapter is used when the transport is hosted outside the standard BtsNtSvc.exe process within Internet Information Services (IIS) using the HTTP transport. The WCF-Custom adapter can be used with either a receive location or a send port. It is used when the transport is hosted inside the standard BtsNtSvc.exe process.  
  
## How does a WCF endpoint relate to BizTalk Server?  
 A WCF endpoint is composed of an address, a binding, and a contract (ABC). Within BizTalk Server, the user specifies the address in the receive location or send port. The binding is dictated by the WCF adapter the user has chosen. The contract is programmer-driven in that it specifies the interface exposed by the endpoint.  
  
 The actual endpoint exists as a receive location to which WCF messages are sent.  There are multiple ways to expose a WCF endpoint in a BizTalk Server application:  
  
- You can use the BizTalk WCF Service Publishing Wizard to publish a BizTalk orchestration as a WCF endpoint.  
  
- You can use the BizTalk WCF Service Publishing Wizard to create a receive location in an existing BizTalk application.  
  
- You can manually create a WCF endpoint by configuring a receive location’s binding and address in code.  In this case the receive location is actually un-typed.  It has a contract that is specified purely in terms of the WCF Message class, allowing it to receive any message format into the MessageBox database.  
  
  Each BizTalk receive location that uses a WCF adapter is exposed as a WCF endpoint into which a WCF client can make a call.  A receive location internally uses its own WCF ServiceHost to allow the different receive locations to be enabled or disabled independently of each other. The lifetime of the service endpoint exists as long as that receive location is enabled. It is because of this lifetime issue that WCF ServiceHosts correspond to receive locations rather than to receive ports. The design of WCF ensures that individual ServiceHosts are not expensive in terms of runtime resources and many can be run within the same executable without any trouble.  
  
  Each BizTalk send port that uses a WCF adapter corresponds to a call made to a WCF service. When there are messages to be sent, BizTalk Server gives the adapter those messages that correspond to the creation of the WCF client proxy within the BizTalk WCF adapter. After the messages are sent the WCF client proxy is released. The WCF lifetime on a send port constantly comes and goes as a proxy is created, used, and torn down.