---
title: "Fault Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "error messages"
  - "ports, error messages"
  - "Catch Exception block [Orchestration Designer], error messages"
  - "error messages, receiving"
  - "messages, errors"
  - "error messages, sending"
ms.assetid: 33d62260-b5e0-4d14-b2d2-996733d588e7
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Fault Messages
Request-response ports can have fault messages associated with them, so that if something goes wrong after a request is sent, the responding service can communicate the error to the requester, in lieu of the response.  
  
 Each operation of a request-response port can handle an arbitrary number of different faults. A fault message can have any message type, but the message type must be unique for the operation, and it must not be the type used by the response in that port operation.  
  
## Receiving fault messages  
 If your port operation sends a request, then receives a response, you can use it to receive one or more different fault message types.  
  
 You can configure a **Catch Exception** block to handle an incoming fault message by selecting the appropriate fault from the request-response port operation as its Exception Object Type.  
  
## Sending fault messages  
 If your port operation receives a response, then sends a request, you can use it to send one or more different fault message types.  
  
 If for example your orchestration encounters an error condition and throws an exception, you can send a fault message from within the **Catch Exception** block that handles the exception. You construct a fault message of an appropriate type to convey the situation to the participating service, and specify that fault message on a Send shape that will use the corresponding fault in the port operation.  
  
## See Also  
 [Exceptions](../core/exceptions.md)