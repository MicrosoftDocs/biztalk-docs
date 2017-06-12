---
title: "WCF Adapters Service Contract Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 079068f6-0448-4315-8f35-0ae1ae15a3eb
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapters Service Contract Reference
The WCF adapters use untyped message contracts when receiving messages. By using the untyped message contract, the WCF adapters can receive any type of WCF messages from clients. You can specify how to create BizTalk messages from incoming WCF messages through the **Inbound BizTalk message body** options in the BizTalk Administration console. The WCF adapters service contracts in the following table are used as the untyped message contracts of the WCF receive adapters.  
  
> [!WARNING]
>  This topic is provided for information only. You can use this information to interpret the instances that WCF performance counters create for the WCF adapters and the auto-generated metadata for the WCF adapters. Do not rely on this information when you create applications.  
  
|Interface|Description|  
|---------------|-----------------|  
|[ITwoWayAsync Interface](../core/itwowayasync-interface.md)|Used for the WCF request-response receive locations. The WCF adapters asynchronously process messages incoming through this interface.|  
|[ITwoWayAsyncVoid Interface](../core/itwowayasyncvoid-interface.md)|Used for the WCF one-way receive locations that do not support a transaction protocol, excluding the WCF-NetMsmq adapter. The WCF adapters asynchronously process messages incoming through this interface.|  
|[ITwoWayAsyncVoidTxn Interface](../core/itwowayasyncvoidtxn-interface.md)|Used for the WCF one-way receive locations that support a transaction protocol, excluding the WCF-NetMsmq adapter. The WCF adapters asynchronously process messages incoming through this interface.|  
|[IOneWayAsync Interface](../core/ionewayasync-interface.md)|Used for the WCF-NetMsmq one-way non-transactional receive locations. The WCF adapter asynchronously processes messages incoming through this interface. **Note:**  The messages incoming through the **IOneWayAsync** interface can be lost because the interface is used for non-transactional datagram channels.|  
|[IOneWayAsyncTxn Interface](../core/ionewayasynctxn-interface.md)|Used for the WCF-NetMsmq one-way transactional receive locations. The WCF adapter asynchronously processes messages incoming through this interface.|  
|[BizTalkServiceInstance Class](../core/biztalkserviceinstance-class.md)|Implements the service contracts that the WCF adapters use to receive incoming messages. The WCF adapters create a separate **ServiceHost** and singleton service object of this class for each receive location to handle client requests for the lifetime of the BizTalk Host instance running WCF receive locations. The service object uses multiple threads to process messages concurrently unless the WCF-NetMsmq receive locations are used with the **Ordered processing** property being selected.|  
  
-   The WCF adapters choose one of the WCF service contracts to receive messages depending on the channel stack configured in the WCF receive locations.  
  
    > [!NOTE]
    >  For the standard WCF adapters, the channel stack is automatically configured by the WCF configuration properties of the receive locations.  
  
     To determine which service contract to use, the WCF adapters invoke the **Binding.CanBuildChannelListener** method with **IReplyChannel**, **IReplySessionChannel**, and **IDuplexSessionChannel** against the binding for the WCF receive locations. If any of the method calls returns **true**, the service contracts starting with **ITwoWayAsync** are used to ensure at-least-once delivery. Otherwise, the service contracts starting with **IOneWayAsync** are used to receive messages. Then the WCF adapters choose the service contracts ending with **Txn** for the following cases:  
  
    -   The **TransactionFlowBindingElement** is added to the channel stack, in which the transaction flow is enabled.  
  
    -   The **MsmqTransportBindingElement** is added to the channel stack, of which the **ExactlyOnce** property is set to **true**.  
  
    -   A binding element implementing the **ITransactedBindingElement** is added to the binding, of which the **TransactedReceiveEnabled** property is set to **true**.  
  
-   If the **OneWayBindingElement** is added for a WCF request-response receive location, messages incoming through the receive locations can be lost because the **OneWayBindingElement** generates a dummy response immediately before dispatching the messages to the WCF adapters.  
  
## See Also  
 [ServiceHost Class](http://go.microsoft.com/fwlink/?LinkId=88630)   
 [Binding.CanBuildChannelListener](http://go.microsoft.com/fwlink/?LinkId=88633)   
 [IReplyChannel Interface](http://go.microsoft.com/fwlink/?LinkId=88636)   
 [IReplySessionChannel Interface](http://go.microsoft.com/fwlink/?LinkId=88638)   
 [IDuplexSessionChannel Interface](http://go.microsoft.com/fwlink/?LinkId=88639)   
 [TransactionFlowBindingElement Class](http://go.microsoft.com/fwlink/?LinkId=88641)   
 [MsmqTransportBindingElement](http://go.microsoft.com/fwlink/?LinkId=88642)   
 [ITransactedBindingElement Interface](http://go.microsoft.com/fwlink/?LinkId=88643)   
 [ITransactedBindingElement.TransactedReceiveEnabled Property](http://go.microsoft.com/fwlink/?LinkId=88645)   
 [OneWayBindingElement Class](http://go.microsoft.com/fwlink/?LinkId=88644)