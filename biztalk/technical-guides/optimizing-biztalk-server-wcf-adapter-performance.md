---
description: "Learn more about: Optimizing BizTalk Server WCF Adapter Performance"
title: "Optimizing BizTalk Server WCF Adapter Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2900c845-15be-4466-8fa0-b51b2486842f
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optimizing BizTalk Server WCF Adapter Performance
This topic provides recommendations for selecting the appropriate WCF adapter or binding type and guidance for applying various WCF adapter configuration options.

## Considerations when choosing which WCF adapter to use or which WCF-Custom/WCF-CustomIsolated binding type to use

-   Do not use message-level security if not strictly required because it increases the size of messages. This in turn can minimize the overall throughput of the solution.

-   When choosing which WCF adapter to use or which WCF-Custom/WCF-CustomIsolated **binding type** to use, carefully consider any application requirements such as compatibility, performance, hosting platform, security, and supported transports. The guidelines listed below are applicable to WCF in general, and are not specific to BizTalk Server:

    -   **BasicHttpBinding** should be used if the WCF service needs to support legacy clients such as WebSphere Web services or .NET 1.1 applications that expect an ASMX Web service. Because BasicHttpBinding does not implement any security by default, if you require message or transport security, you should configure it explicitly on this binding. Use BasicHttpBinding to expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1. When configuring transport security, BasicHttpBinding defaults to use no credentials just like a classic ASMX Web service. BasicHttpBinding allows you to host the WCF service in IIS 7.5 or IIS 7.0.

    -   **WsHttpBinding** should be used if the WCF service will be called by WCF clients over the Internet. WsHttpBinding is a good choice for Internet scenarios in which you do not have to support legacy clients that expect an ASMX Web service and WsHttpBinding allows you to host the WCF service in IIS 7.5 or IIS 7.0. If you do need to support legacy clients, consider using BasicHttpBinding instead.
        WsHttpBinding should be used when you need to expose WCF Receive Locations or adopt Send Ports which support WS-* Protocols like WS-Security or WS-AtomicTransactions.

    -   **NetTcpBinding** is an excellent choice if you need to support clients within your intranet. NetTcpBinding is a good choice for intranet scenarios if transport performance is important to you, and if it is acceptable to host the service in a Windows service instead of in IIS. Use this binding when you want to provide a secure and reliable binding environment for .NET-to-.NET cross-machine communication. Note that the NetTcpBinding  must be hosted in a Windows service or in IIS 7.5/7.0.

    -   **NetNamedPipeBinding** should be used if you need to support WCF clients on the same computer as your service. This binding provides a secure and reliable binding environment for cross-process, same-computer communication. Use this binding when you want to make use of the NamedPipe protocol. Note that the NetNamedPipeBinding must be hosted in a Windows service or in IIS 7.5/7.0.

    -   **NetMsmqBinding** should be used if you need to support disconnected queuing. Queuing is provided by using Message Queuing (also known as MSMQ) as a transport, which enables support for disconnected operations, failure isolation, and load leveling. You can use NetMsmqBinding when the client and the service do not have to be online at the same time. You can also manage any number of incoming messages by using load leveling. Message Queuing supports failure isolation, where messages can fail without affecting the processing of other messages. Note that the NetMsmqBinding  must be hosted in a Windows service or in IIS 7.5/7.0.

    -   **WsDualHttpBinding** should be used if you need to support a duplex service. A duplex service is a service that uses duplex message patterns, thus providing the ability for a service to communicate back to the client via a callback. Note that the WsDualHttpBinding  must be hosted in a Windows service or in IIS 7.5/7.0.

## WCF Binding Comparison
 Bindings provide a mechanism for configuring channel stacks. A binding creates a process to build a channel stack using a transport channel, a message encoder, and a set of protocol channels. Windows Communication Foundation ships with numerous built-in bindings that come preconfigured to address most common communication scenarios.

|Binding Class Name|Transport|Message Encoding|Security Mode|Reliable Messaging|Transaction Flow (disabled by default)|
|------------------------|---------------|----------------------|-------------------|------------------------|----------------------------------------------|
|BasicHttpBinding|HTTP|Text|None|Not supported|Not supported|
|WSHttpBinding|HTTP|Text|Message|Disabled|WS-AtomicTransactions|
|NetTcpBinding|TCP|Binary|Transport|Disabled|OleTransactions|
|NetNamedPipesBinding|Named Pipes|Binary|Transport|Not supported|OleTransactions|
|NetMsmqBinding|MSMQ|Binary|Message|Not supported|Not supported|
|CustomBinding|You decide|You decide|You decide|You decide|You decide|

 You can select a particular binding based on your communication needs. For example:

-   **BasicHttpBinding** is designed for interoperability with simple Web services. BasicHttpBinding uses HTTP for the transport and text for the message encoding.

-   **WSHttpBinding** is designed for interoperability with more advanced Web services that might take advantage of different WS-* protocols.  WSHttpBinding also uses HTTP for the transport and text for the message encoding.

-   **NetTcpBinding** and **NetNamedPipeBinding** are designed for efficient and perform ant communication with other WCF applications across machines or on the same machine respectively.

-   If you need maximum flexibility by using one or multiple custom protocol channels at runtime, you can use the **CustomBinding** that gives you the possibility to decide which binding elements compose your binding.

> [!NOTE]
>  Bindings have different characteristics in terms of response time and throughput. So, the general advice to increase performance is using the NetTcpBindind and NetNamesPipeBinding when possible.

## Use the TCP transport and binary message encoding to maximize WCF adapter throughput and minimize WCF adapter latency
 Use the WCF-NetTcp adapter when possible to maximize throughput. The WCF-NetTcp adapter uses TCP/IP transport protocol and binary message encoding which together provide improved performance as compared to other WCF-* adapters.

 Alternatively, you can configure the WCF-Custom (or WCF-CustomIsolated adapter for Receive Locations) with a **customBinding** binding type. Then, add the **binaryMessageEncoding** binding extension to implement binary message encoding and the **tcpTransport** binding extension to implement TCP/IP as the message transport protocol. This approach is very flexible because it allows you to select and configure only the binding elements you need and to create custom channels to extend the default behavior of the BizTalk Messaging Engine. If you implement the WCF-Custom adapter with the **customBinding** binding type, specify these values for the binding extension Configuration parameters to maximize throughput and minimize latency.

 **Send Port Configuration Values:**

|Setting|Default value|Recommended value|
|-------------|-------------------|-----------------------|
|**TcpTransportBindingElement.ConnectionPoolSettings.maxOutboundConnectionsPerEndpoint** - Gets or sets the maximum number of outbound connections for each endpoint cached in the connection pool. This limits the number of connections that are cached for each unique remote endpoint. If this value is exceeded by having more active client connections, the service may appear unresponsive to the client, and this value should be adjusted to accommodate the maximum number of expected connections that are cached for each unique remote endpoint. For more information about this property, see [TcpConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint Property](https://go.microsoft.com/fwlink/?LinkId=157737) (https://go.microsoft.com/fwlink/?LinkId=157737) on MSDN.|10|Try >= 20|

 **Receive Port Configuration Values:**

|Setting|Default value for .NET Framework 4|Recommended value for .NET Framework 4|Default value for .NET Framework 3.5|Recommended value for .NET Framework 3.5|
|-------------|----------------------------------------|--------------------------------------------|------------------------------------------|----------------------------------------------|
|**TcpTransportBindingElement.MaxPendingAccepts** - Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service. For scenarios with high levels of simultaneous connection initiations, this value may be inadequate and should be adjusted along with the **MaxPendingConnections** property to handle higher levels of concurrent client connection attempts. It should not be necessary to set this property to a value greater than the number of processors present in the machine hosting the service. For more information about this property, see [ConnectionOrientedTransportBindingElement.MaxPendingAccepts Property](https://go.microsoft.com/fwlink/?LinkId=157738) (https://go.microsoft.com/fwlink/?LinkId=157738) on MSDN.|1|2*ProcessorCount|1|Try >= 20|
|**TcpTransportBindingElement.MaxPendingConnections** - Gets or sets the maximum number of connections awaiting dispatch on the service. This limits the number of simultaneous client connections awaiting dispatch. If this value is too low, client connection attempts may be rejected by the service. If it is too high, the service may appear slow or unresponsive to clients during heavy load periods. This property should be set to a value that allows the service to run at full capacity, and no higher. When a higher layer in the stack calls **AcceptDispatch**, that connection is removed from the queue of connections awaiting dispatch. For more information about this property, see [ConnectionOrientedTransportBindingElement.MaxPendingConnections Property](https://go.microsoft.com/fwlink/?LinkId=157735) (https://go.microsoft.com/fwlink/?LinkId=157735) on MSDN.|10|16*ProcessorCount|10|Try >= 20|
|**TcpTransportBindingElement.ListenBacklog** - Gets or sets the maximum number of queued connection requests that can be pending. **ListenBacklog** is a socket-level property that describes the number of "pending accept" requests to be queued. Ensure that the underlying socket queue is not exceeded by the maximum number of concurrent connections. For more information about this property see [TcpTransportBindingElement.ListenBacklog Property](https://go.microsoft.com/fwlink/?LinkId=157734) (https://go.microsoft.com/fwlink/?LinkId=157734) on MSDN.|10|16*ProcessorCount|10|Try >= 20|

 **Add the ServiceThrottlingBehavior service behavior to a WCF-Custom or WCF-CustomIsolated Receive Location and use the following settings:**

> [!NOTE]
>  Before any elements of the ServiceThrottlingBehavior service behavior can be modified, you must first add the **serviceThrottling** behavior extension to the **Behaviors** tab of the **WCF-Custom\* Transport Properties** dialog box. To add serviceThrottling to the list of Behaviors, select the **Behaviors** tab of the **WCF-Custom\* Transport Properties** dialog box, right-click **ServiceBehavior** under **Behavior**, click **Add extension**, select **serviceThrottling**, and then click **OK**. Then click to select the properties available under **ServiceThrottlingElement** and change the value for the properties as needed.

|Setting|Default value for .NET Framework 4|Recommended value for .NET Framework 4|Default value for .NET Framework 3.5|Recommended value for .Net Framework 3.5|
|-------------|----------------------------------------|--------------------------------------------|------------------------------------------|----------------------------------------------|
|**ServiceThrottlingBehavior.MaxConcurrentCalls** - Gets or sets a value that specifies the maximum number of messages actively processing across a **ServiceHost**. The **MaxConcurrentCalls** property specifies the maximum number of messages actively processing across a **ServiceHost** object. Each channel can have one pending message that does not count against the value of **MaxConcurrentCalls** until WCF begins to process it. For more information about this property, see [ServiceThrottlingBehavior.MaxConcurrentCalls](https://go.microsoft.com/fwlink/?LinkId=157838) (https://go.microsoft.com/fwlink/?LinkId=157838) on MSDN. The default value for the BizTalk WCF-Custom and WCF-CustomIsolated receive adapters **MaxConcurrentCalls** property is **16** per CPU. **Note:**  BizTalk Server WCF receive adapters other than the WCF-Custom and WCF-CustomIsolated adapter expose a **Maximum Concurrent Calls** property on the **Binding** tab of the **WCF-\* Transport Properties** dialog box to configure this behavior. The default value of the **Maximum Concurrent Calls** behavior is **200**.|16*ProcessorCount|16*ProcessorCount|-   16 for the BizTalk WCF-Custom and WCF-CustomIsolated receive adapters.<br />-   200 for the other WCF receive adapters.|-   Try >= 200 for the WCF-Custom and WCF-CustomIsolated receive adapters.<br />-   Try > 200 for the **Maximum Concurrent Calls** property on the **Binding** tab of the **WCF-\* Transport Properties** dialog box for BizTalk Server WCF receive adapters other than the WCF-Custom and WCF-CustomIsolated adapter.|
|**ServiceThrottlingBehavior.maxConcurrentInstances** - Gets or sets a value that specifies the maximum number of **InstanceContext** objects in the service that can execute at once. The **MaxConcurrentInstances** property specifies the maximum number of **InstanceContext** objects in the service. It is important to keep in mind the relationship between the **MaxConcurrentInstances** property and the **InstanceContextMode** property. If **InstanceContextMode** is PerSession, the resulting value is the total number of sessions. If **InstanceContextMode** is PerCall, the resulting value is the number of concurrent calls. If a message arrives while the maximum number of **InstanceContext** objects already exist, the message is held until an **InstanceContext** object closes. For more information about this property, see [ServiceThrottlingBehavior.MaxConcurrentInstances Property](https://go.microsoft.com/fwlink/?LinkId=157897) (https://go.microsoft.com/fwlink/?LinkId=157897) on MSDN. The default value for the WCF-Custom and WCF-CustomIsolated receive adapter MaxConcurrentInstances property is **116** per CPU. **Note:**  Since WCF receive locations are implemented as instances of the BizTalkServiceInstance class contained in the Microsoft.BizTalk.Adapter.Wcf.Runtime.dll assembly and since this class is marked as ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Multiple). all incoming requests are managed by the same singleton object and this parameter is ignored. So setting the maxConcurrentInstances property on certain WCF-Custom receive locations has no effect, since the number of active instances is always equal to 1.|116*ProcessorCount|116*ProcessorCount|26|Try >= 200|
|**ServiceThrottlingBehavior.MaxConcurrentSessions** - The **MaxConcurrentSessions** property gets or sets the maximum number of sessions a **ServiceHost** object can accept at one time. It is important to understand that sessions in this case does is not limited to only channels that support reliable sessions. Each listener object can have one pending channel session that does not count against the value of **MaxConcurrentSessions** until WCF accepts the channel session and begins processing the channel session messages. This property is most useful in scenarios that make use of sessions. When this property is set to a value less than the number of client threads, the requests from multiple clients may get queued in the same socket connection. The requests from the client that has not created a session with the service will be blocked. They will remain blocked until the service closes its session with the other clients, if the number of open sessions on the service has reached the value specified for **MaxConcurrentSessions**. The client requests that are not served are then timed out, and the service closes the session. To avoid this situation, consider running the client threads from different application domains so that the request messages are accepted by different socket connections. For more information about this property, see [ServiceThrottlingBehavior.MaxConcurrentSessions Property](https://go.microsoft.com/fwlink/?LinkID=157864) (https://go.microsoft.com/fwlink/?LinkId=157864) on MSDN.|100*ProcessorCount|100*ProcessorCount|10|Try >= 200|

 When modifying port configuration settings apply changes methodically; modify each parameter individually and, test the effects of the change on performance and overall stability. As always, the proper value to apply depends on the particular scenario: if a value is set too low, scalability can be reduced; whereas if a value is set too high, the application requirement may exceed the capacity of physical resources on the computer. In addition, since these properties are related, they should be set in a consistent and coherent way. For more information about using ServiceThrottlingBehavior to control WCF Service Performance, see [Using ServiceThrottlingBehavior to Control WCF Service Performance](https://go.microsoft.com/fwlink/?LinkId=157908) (https://go.microsoft.com/fwlink/?LinkId=157908) on MSDN.

## See Also
 [Optimizing BizTalk Server Performance](../technical-guides/optimizing-biztalk-server-performance.md)
