---
description: "Learn more about: Messaging Engine Interfaces"
title: "Messaging Engine Interfaces"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Messaging Engine Interfaces
There are three public interfaces that adapters can use to allow interaction with the Messaging Engine. These are outlined in the following sections.  
  
## IBTTransportProxy  
 Adapters always interact with the Messaging Engine by using their own transport proxy. The transport proxy is used for operations such as creating batches, getting the message factory, and registering isolated receivers with the engine.  
  
## IBTTransportBatch  
 This interface is provided by the Messaging Engine, and defines methods that adapters can use to operate on batches of messages. The Messaging Engine processes batches asynchronously.  
  
## IBTDTCCommitConfirm  
 Adapters using explicit Microsoft Distributed Transaction Coordinator (MSDTC) transactions on batches must use this interface to notify the engine of the outcome of the transaction using this interface.
