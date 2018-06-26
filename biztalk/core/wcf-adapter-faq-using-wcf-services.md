---
title: "WCF Adapter FAQ: Using WCF Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: befa2268-8a65-465f-8086-70a66808845e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapter FAQ: Using WCF Services
## How does BizTalk Server use its WCF adapters to access WCF services?  
 BizTalk WCF adapters are configured in BizTalk Server through either a WCF receive location or a send port. When a receive location using a WCF adapter is enabled, a single ServiceHost instance is instantiated and initialized for each receive location. The ServiceHost runs a generic service that accepts incoming WCF messages, and converts them to BizTalk messages before publishing them to the BizTalk MessageBox database. The generic ServiceHost service is internal to the WCF BizTalk receive adapter implementation and exposes a typeless contract. In WCF, a typeless contract consists of operation signatures that take a single parameter of type WCF System.ServiceModel.Channel.Message.  
  
 The operation  of a WCF service should be marked as IsOneWay=false if they are to be accessed by a BizTalk send port even if there is no data to return. The operations on the client-side contract should be annotated with IsOneWay=false and ReplyAction=”*”.  Additionally all calls from the client should be marked at IsOneWay=”false”. A two-way service operation may return a value of type Message. The exception to this is using the WCF-NetMsmq adapter since it executes a one-way operation that posts a message into an MSMQ queue. In this case the send port can be one-way and any service operation marked as IsOneWay=true.  
  
 It may be a little confusing that it is also possible in WCF to define an isOneWay=false OperationContract on a method that actually returns void. In such a situation there is actually a message returned on the wire created by the WCF runtime for you.  
  
 The BizTalk WCF adapters make use of this feature. When you specify a one-way BizTalk port you actually get a void method with isOneWay=false within the implementation of the WCF adapter. The point is that a BizTalk one-way port, when using a direct channel such as HTTP or net.tcp, will actually correspond to an isOneWay=false OperationContract. Queued channels such as net.msmq are different in that a one-way BizTalk port does happen to talk to an isOneWay=true OperationContract. The situation is different because the WCF dispatcher is using a transaction against the channel.  
  
## How do you create and use a custom binding with a WCF custom adapter?  
 A WCF CustomBinding consists of a collection of BindingElements. A CustomBinding can be created by pulling together pre-existing BindingElements (for example, combining a pre-existing Transport with a pre-existing Encoder from another source). Or it can be created by combining a pre-existing BindingElement with a newly written custom BindingElement. In code a CustomBinding can be built from these component BindingElements by adding them programmatically. WCF also allows this construction through .NET Configuration (config files). By using BizTalk Server this CustomBinding can be created through the BizTalk WCF Custom adapter.  
  
 The BizTalk WCF Custom adapter not only allows you to build a new binding from BindingElements but also lets you configure a new binding directly. It also allows you to configure behaviors on standard bindings. This is particularly useful because writing custom behaviors is much easier than writing new BindingElements objects.  
  
 Building a BindingElement is an involved development exercise and the best source of reference for it is the WCF samples at  HYPERLINK "<http://go.microsoft.com/fwlink/?LinkId=142449>" \t "_blank" http://go.microsoft.com/fwlink/?LinkId=142449. To create a custom BindingElement you create a class that derives from BindingElement. A new BindingElement will have to be in a new assembly. This assembly must be installed into the Global Assembly Cache (GAC) of the administration computer where the BizTalk Host, send port, and receive location are configured. To associate a custom binding with a specific send port or receive location, you first need to add it to the \<bindingElementExtensions\> section of the machine.config file on the same computer.  
  
 After making that change you can then bring up the **Transport Properties Configuration** dialog box to configure the binding.  
  
1. On the **Binding** tab, for Binding type, select **customBinding**.  
  
2. In the **Binding** pane, right-click **CustomBindingElement**, and select **Add Extension**.  
  
3. Select the binding element you specified in the machine.config file and configure the binding as required. It is now ready to use for message transmission or receipt.  
  
   BizTalk does very limited validation for a custom binding when it has been added in this manner. Therefore, it is important to ensure the binding elements are listed in the correct order. The binding element you want invoked first at runtime must be on the bottom of the CustomBindingElement binding tree in the dialog box. The list of BindingElements must contain a Transport and that Transport must be at the bottom of the list. The set of BindingElements may also contain an Encoder. For more information, see the WCF documentation on binding elements at [http://go.microsoft.com/fwlink/?LinkId=142449](http://go.microsoft.com/fwlink/?LinkId=142449).  
  
## What is a WCF custom behavior and how do I use one with BizTalk Server?  
 One of the advantages of using WCF as a message communication mechanism is the opportunity to extend the functionality of its services by using custom code. Custom behavior extensions are one of the features that differentiate WCF from other Web services technologies in the market.  
  
 There are different points within the flow of a WCF message to intercept and execute custom processing before a message reaches its final destination. WCF custom behavior extensions are one such type of interception mechanism and can be used to extend WCF service or client functionality at different levels of granularity. Custom behavior extensions can exist at both the WCF service and client levels. Configuring a behavior on the call stack to a WCF service has no influence on the communication binding used to make the call. In fact, behaviors are typically invisible to the client because they are not displayed in the metadata a service publishes. The client typically has no idea that the behaviors are executing during a call to a WCF operation.  
  
 The ability to easily implement custom processing in a call to a WCF service is one of the main reasons why WCF is such a rich programming paradigm compared to other ways of communication between Web applications. This custom processing can take almost any form as dictated by extensibility requirements within a Web application. Developers can create custom extensions that inspect and validate service configuration or modify runtime behavior in WCF client and service applications. Behaviors can supplement normal message processing, modify the message during processing, scrutinize certain configuration criteria and take appropriate action, validate identities of the caller and pass the message on if it is successful, etc. Because it is truly a custom processing mechanism you implement whatever extensibility your application needs.  
  
 To use a WCF custom behavior in BizTalk Server you will configure it by using the **Behavior** tab for the WCF-Custom or WCF-CustomIsolated adapter for a receive location or a send port.