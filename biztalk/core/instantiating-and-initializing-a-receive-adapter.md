---
title: "Instantiating and Initializing a Receive Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5cb5ba7-e2b5-49d2-adf5-a8df0bb81def
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Instantiating and Initializing a Receive Adapter
Immediately after a receive adapter is instantiated it is initialized by the Messaging Engine, the engine calls QueryInteraface for IBTTransportControl. It then calls IBTTransportControl<strong>.Initialize</strong> passing in the adapter's transport proxy, which the adapter persists in a member variable. Next the engine calls **QueryInterface** for **IPersistPropertyBag**. This is an optional interface; if the adapter implements it, the handler configuration is passed to the adapter in the **Load** method call. The final stage of initializing a receive adapter involves passing the endpoint configuration to the adapter. During this phase the engine calls **IBTTransportConfig.AddReceiveEndpoint** once for each active endpoint, passing in the URI for the endpoint, the adapter specific configuration for the endpoint, and the BizTalk configuration for that endpoint.  
  
 The following figure illustrates this sequence of API calls. The adapter implements the interfaces shown in blue.  
  
 ![](../core/media/sequence-of-init-calls.gif "Sequence_of_init_calls")  
  
 **Implementation Tip:** In general, adapters should not block the Messaging Engine in calls such as **IBTTransportControl.Initialize**, **IPersistPropertyBag.Load**, and **IBTTransportConfig.AddReceiveEndpoint**. Performing excessive processing in these calls can have a negative impact on service startup time.  
  
 All receive adapters that have one or more associated receive locations are created at service startup. All receive adapters are asynchronous and support batching. They can be in-process or isolated. For additional information about receive adapter variables, see [Adapter Variables](../core/adapter-variables.md).