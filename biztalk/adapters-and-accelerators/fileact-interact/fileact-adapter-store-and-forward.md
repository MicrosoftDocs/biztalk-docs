---
description: "Learn more about: FileAct Adapter Store and Forward"
title: "FileAct Adapter Store and Forward"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FileAct Adapter Store and Forward
In Store and Forward (SnF) mode, files are delivered to queue at send time, and are retrieved from the queue by the destination. Intermediate responses are returned by SWIFTNet to the sender until the file is safely delivered to the destination.  
  
## Sending Using SnF  
 If you create a one-way send port, the adapter works in SnF mode and sends messages to the queue.  
  
## Receiving Using SnF  
 SnF FileAct operates in Push mode. This is a run-time option.  
  
 Before being able to retrieve messages from a queue, SWIFTNet SnF should receive a request to acquire the queue. This is accomplished by the receive adapter invoking the out-of-proc COM+ component. After a successful acquire, a session is created. The queue will then be opened in the mode specified in the Request. All messages will be returned to the physical node which issued the request.  
  
 Messages are delivered in the order specified (note that InterAct and FileAct transmissions can be interspersed, and arranged by priority.) The sequencing of messages, however, is dependent on the time that they were stored. In the case of FileAct, this is the time that the file storage is completed, not when it started.  
  
### Push a File From the Queue  
 The FileAct adapter (server) receives a HandleFileRequest from SWIFTNet, containing the queue, session and sequence information. The server responds with a HandleFileResponse.  
  
 The server then issues FetchFileRequest and the file is delivered to the server.  
  
## See Also  
 [FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)   
 [FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md)   
 [FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md)   
 [FileAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-security-architecture.md)   
 [FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md)   
 [FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md)   
 [FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md)   
 [FileAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)
