---
description: "Learn more about: FRR NAK Handler Sample"
title: "FRR NAK Handler Sample"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FRR NAK Handler Sample
The FRR NAK Handler sample demonstrates how to create a custom handler to process messages that FIN Response Reconciliation (FRR) has correlated with SWIFT responses. This custom handler processes messages that FRR has correlated with a MTS21_FIN_ACKNAK negative-acknowledgment message, which indicates that SWIFT did not successfully receive the message from A4SWIFT. The custom handler adds an error object to the message, making the message a two-part message, and promotes the properties that cause the message-repair orchestration to pick up the message. As a result, a repairer can fix the message and resend it to SWIFT Alliance Access (SAA).  
  
 **Sample Components**  
  
 The FRR NAK Handler sample includes the following components:  
  
- **RepairSWIFTRejectedMessage.odx.** This orchestration is the custom handler that processes a message that SWIFT could not successfully receive, routing it to the message-repair orchestration so a repairer can fix and resend the message.  
  
- **RepairSWIFTRejectedMessage.btproj.** This project includes RepairSWIFTRejectedMessage.odx and the references required for the project to build and deploy.  
  
- **RepairSWIFTRejectedMessage.sln.** This solution includes the RepairSWIFTRejectedMessage.btproj project.  
  
  This section contains:  
  
- [Implementing the FRR NAK Handler Sample](../../adapters-and-accelerators/accelerator-swift/implementing-the-frr-nak-handler-sample.md)  
  
- [How the FRR NAK Handler Sample Works](../../adapters-and-accelerators/accelerator-swift/how-the-frr-nak-handler-sample-works.md)  
  
