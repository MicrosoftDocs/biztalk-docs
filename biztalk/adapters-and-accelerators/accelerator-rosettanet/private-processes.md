---
title: "Private Processes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private processes, trading partners"
  - "private processes, about private processes"
  - "private processes, orchestrations"
  - "private processes"
  - "orchestrations, private-process orchestrations"
  - "trading partners, private processes"
  - "BTARN, private processes"
  - "business processes, private processes"
ms.assetid: 0c5895eb-22c1-431f-a769-ae6ca05d1e45
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Private Processes
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] implements business processes that are internal to an organization as private processes. Public processes handle business processes that involve integration with trading partners. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] isolates service-content processing and back-end integration (in the private process) from RosettaNet Implementation Framework (RNIF) handling (in the public process).  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implements private processes as long-running BizTalk orchestrations. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses one private-process orchestration on the initiator side and one on the responder side. Each private process interprets and processes the service-content message part, either incoming or outgoing. The private process sends the service content to, or receives it from, the public process. A private process does not handle headers, and does not perform RNIF processing. It leaves that to the public process.  
  
 In an enterprise scenario, there would typically be one private process for each PIP message schema. However, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes two private-process orchestrations that can process any PIP message. One orchestration is for the initiator process (PrivateInitiator.odx, see [PrivateInitiator Sample &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/privateinitiator-sample.md)) and one is for the responder process (PrivateResponder.odx, see [PrivateResponder Sample &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/privateresponder-sample.md)). You will have to customize the private processes to adapt [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] to your specific business processes.  
  
 The SDK also includes a process that implements a PIP-specific private responder process incorporating a business rule (PIP3A4PrivateResponder.odx, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)).  
  
 The private process changes the format of the service content from the back-end line-of-business (LOB) format to XML. As soon as it is in XML format, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processes the service content, and the public process adds RNIF-compliant headers to the service content for transmission.  
  
 The private process connects to the back-end line-of-business applications through the MessageToLOB and MessagesFromLOB tables in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database. This database handles the communication between [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] and the LOB applications. The LOB application uses an interface to gain access to the database tables.  
  
## In This Section  
  
-   [Initiator Private Process](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md)  
  
-   [Responder Private Process](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)