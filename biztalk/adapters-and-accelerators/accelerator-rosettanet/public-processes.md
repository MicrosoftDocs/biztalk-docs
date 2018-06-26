---
title: "Public Processes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "public processes, orchestrations"
  - "business processes, public processes"
  - "public processes, trading partners"
  - "BTARN, public processes"
  - "orchestrations, public-process orchestrations"
  - "public processes"
  - "trading partners, public processes"
  - "public processes, about public processes"
ms.assetid: 5ccc7449-5741-4d49-beb6-567bcd93f679
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Public Processes
Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] implements business processes that involve integration with trading partners as public processes. It implements business processes that are internal to an organization as private processes. Using public and private processes isolates RosettaNet Implementation Framework (RNIF) handling (in the public process) from the service content processing and back-end integration (in the private process).  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implements public processes as long-running BizTalk orchestrations. One public-process orchestration runs on the initiator side and one on the responder side. The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program provides versions of the initiator and responder public-process orchestrations for both RNIF 1.1 and RNIF 2.01.  
  
 These public-process orchestrations implement all RNIF processes. Public processes hide the complexity of RNIF from the rest of the components. Besides enforcing the RNIF-compliant message flow, the public process also determines default-tracking settings and provides process state information at run time. It does not process the service content of a message. The private process does this.  
  
 Each trading partner agreement references a single public process to initiate or respond to Partner Interface Process (PIP) actions. However, the public processes are PIP-agnostic.  
  
 The RosettaNet specifications dictate the design of the public process. It is recommended that you do not modify a public process. The public-process orchestration is versioned and signed. If you modify a public process, it will no longer be RNIF-compliant.  
  
## In This Section  
  
-   [Initiator Public Process](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md)  
  
-   [Responder Public Process](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)