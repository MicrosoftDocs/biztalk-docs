---
title: "FileAct Adapter Real-Time Local Primitives | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef4da4f8-3de2-4d35-8f8a-1e12937e52a1
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FileAct Adapter Real-Time Local Primitives
Local primitives involve two messages each, which are exchanged between the client SWIFTNet Link (SNL) and the local FileAct subsystem.  
  
 The following figure shows the FileAct local primitives.  
  
 ![FileAct local primitives](../../adapters-and-accelerators/fileact-interact/media/67ca0c3b-3c81-401d-87cb-473c68cae63f.gif "67ca0c3b-3c81-401d-87cb-473c68cae63f")  
  
## Get Status for a Single Transfer  
 The Get Status primitive retrieves status information concerning one transfer from the local persistent context.  
  
## Subscribe to Transfer Events  
 Progressive transfer status information may be received on an event-by-event basis by using the Subscribe Event primitive. Each file transfer may be linked to a named entity called an event endpoint during the negotiation. An event server that invokes the Subscribe Event primitive directs all the event reports for one such an event endpoint to itself.  
  
 An event server can subscribe to characteristics (different levels of detail, as well as to different event types).  
  
 An event server may invoke the primitive multiple times to subscribe to multiple event endpoints. Only one event server may subscribe to any particular event endpoint at a given time. Additionally, an event server can invoke the primitive multiple times for the same event endpoint for changing the characteristics.  
  
## Receive Transfer Events  
 Receive Transfer Events is the primitive that handles the event-by-event status information concerning transfers-in-progress. It responds to the terms of a subscription that is set up by the Subscribe Event primitive. This primitive can be implemented at the sending or receiving side of a transfer.  
  
## Abort Transfer  
 A user application may abort a transfer-in-progress using the Abort primitive. The Abort primitive is a primitive that may be exercised from either the sending-side or the receiving-side of a transfer-in-progress. When initiating or accepting a transfer, each side has the option of establishing a transfer key that serves as an access key to protect that transfer from its own side. If a transfer key is established for a transfer-in-progress, it may not be aborted from that side without supplying the transfer key value in the exercise of the Abort primitive.  
  
## See Also  
 [FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md)   
 [FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [FileAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)