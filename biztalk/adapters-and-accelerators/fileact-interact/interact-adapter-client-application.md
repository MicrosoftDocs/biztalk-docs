---
title: "InterAct Adapter Client Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdab4624-0fc2-42a3-9867-8f77e144b40c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# InterAct Adapter Client Application
InterAct adapter client application request messages are XML documents passed from the client application to the client-side SWIFTNet Link (SNL). Messages of this type occur as the first part of the SWIFTNet Request/Response primitives exercised on the client side.  
  
 This topic describes the SwInt:ExchangeRequest message. It is used for “synchronous” client-side calls to SWIFTNet. In this context, “synchronous” means that the function call blocks the client application, forcing it to wait until the Response is received from the server-side application. (Or, alternatively, an error condition occurs and that error is reported back to the client.)  
  
 The cryptographic blocks (SwSec:Crypto), if they exist, contain the results of message signing and/or verification processing. Also, at certain processing stages, they may contain instructions that direct cryptographic processing that is to be performed by the SNL.  
  
## InterAct Adapter Payload Format  
 The Request Payload contains the substance of the business message. The structure of the payload must conform to the requirements of well-formed XML (this simply means that the payload does not break the XML parsing, but as such, it does not have to use the XML document structure). If SWIFTNet Message Validation is applied, then there are other structural requirements to which the payload must conform. Aside from that, the payload structure and contents are determined by the business application.  
  
## See Also  
 [InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [InterAct Adapter Messages for Business Exchange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [InterAct Adapter Non-Repudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)