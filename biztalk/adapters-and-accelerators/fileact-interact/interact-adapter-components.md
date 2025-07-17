---
description: "Learn more about: InterAct Adapter Components"
title: "InterAct Adapter Components"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# InterAct Adapter Components
The InterAct adapter has a client and a server component. Note that there may be an A4SWIFT (minimal) installation on the same computer as the SWIFT Alliance Gateway (SAG) if it is running Windows Server. Also note that the SWIFTNet Link (SNL) may be on a separate computer from the SAG. The remote application programming interface (API) host adapter provided by SWIFT is used to communicate from A4SWIFT to the SAG, regardless of the location of the components.  
  
 The figure below shows where the components comprising the entire adapter and communications chain related to the InterAct adapter reside.  
  
 ![InterAct components](../../adapters-and-accelerators/fileact-interact/media/cf257c5a-3668-4aff-bce9-7acc6eb672bd.gif "cf257c5a-3668-4aff-bce9-7acc6eb672bd")  
  
 In the following figure, the client application uses A4SWIFT and the InterAct adapter. BizTalk Server is the middleware, which communicates to the remote API host adapter over TCPIP.  
  
 ![InterAct client application](../../adapters-and-accelerators/fileact-interact/media/7aeada39-6264-498b-92e8-303eb0cf369b.gif "00001111-aaaa-2222-bbbb-3333cccc4444")  
  
 In the following figure, the server application uses A4SWIFT and the InterAct adapter. BizTalk Server is the middleware, which communicates to the remote API host adapter over TCPIP.  
  
 ![InterAct server application](../../adapters-and-accelerators/fileact-interact/media/51cbae6a-41e9-4a50-9574-5e86bc04ddba.gif "51cbae6a-41e9-4a50-9574-5e86bc04ddba")  
  
## See Also  
 [InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct Adapter Messages for Business Exchange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md)   
 [InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [InterAct Adapter Non-Repudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)
