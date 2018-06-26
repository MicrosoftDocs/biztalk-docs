---
title: "Interfaces for an In-Process Receive Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ed668d9-7512-4026-a8f3-df05aeed4df6
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Interfaces for an In-Process Receive Adapter
The Messaging Engine instantiates and configures in-process adapters, passing in the transport proxy to allow the adapter to access its functionality. To enable configuration and binding to the transport proxy, adapters must implement the following configuration interfaces:  
  
- **IBTTransport**  
  
- **IBTTransportControl**  
  
- **IBTTransportConfig**  
  
- **IBaseComponent**  
  
  Optionally if the adapter wants to receive handler information during initialization it needs to implement **IPersistPropertyBag**.  
  
  The Messaging Engine creates an instance of an adapter, initializes it, and sets the configuration of receive locations. The Messaging Engine passes a property bag to an adapter on the **AddReceiveEndpoint** method call. The property bag contains the configuration for the receive location and receive handler. The configuration is stored in the database in the form of an XML-styled property bag. The Messaging Engine reads the XML and rehydrates a property bag from the XML. After at least one endpoint (receive location) is added, the adapter can start submitting messages.  
  
> [!NOTE]
>  Adapters should not block Messaging Engine calls such as **IBTTransportControl.Initialize**, **IPersistPropertyBag.Load**, and **IBTTransportConfig.AddReceiveEndpoint**. Performing excessive processing in these calls will affect service startup time.  
  
 The following figure shows the object interactions involved in creating an in-process receive adapter.  
  
 ![](../core/media/ebiz-sdk-devadapter11.gif "ebiz_sdk_devadapter11")  
Workflow for an in-process receive adapter  
  
## See Also  
 [Adapter Variables](../core/adapter-variables.md)   
 [Developing a Receive Adapter](../core/developing-a-receive-adapter.md)   
 [Instantiating and Initializing a Receive Adapter](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [Interfaces for an Isolated Receive Adapter](../core/interfaces-for-an-isolated-receive-adapter.md)   
 [Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md)   
 [Interfaces for a Transactional Batch-Supported Receive Adapter](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)   
 [Interfaces for a Synchronous Request-Response Receive Adapter](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)