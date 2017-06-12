---
title: "FIN Response Reconciliation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ACKs"
  - "FRR"
  - "FIN Response Reconciliation"
  - "SAA"
  - "NAKs"
  - "FRR, about FRR"
  - "acknowledgements"
  - "FIN Response Reconciliation, about FIN Response Reconciliation"
  - "FIN Response Reconciliation, acknowledgements"
ms.assetid: 987b932b-e487-4ca8-acd0-410d71df8e6d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FIN Response Reconciliation
The FIN Response Reconciliation (FRR) feature of [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reconciles a FIN response with the corresponding original message sent by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. This establishes the status of the original message, and enables [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to take steps based upon that status. Without reconciliation, this would not be possible. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] would know that it successfully (or unsuccessfully) sent the original message to SAA, and it would have the response that it received from SAA, indicating the status of the transmission, but it would not be able to make the connection between the two. FRR establishes that connection.  
  
 FIN responses are acknowledgments (ACKs) or negative acknowledgments (NAKs) sent by SAA to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], or sent by the SWIFT network to SAA and then forwarded by SAA to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. The presence or absence of these acknowledgments defines the business status of the message. You can monitor this status through Business Activity Monitoring (BAM) reporting.  
  
 You can also implement custom application behavior around FRR. A custom handler can implement your own logic for handling reconciled sets of FIN responses. For an example of a custom handler that processes messages that FRR has correlated with a MTS21_FIN_ACKNAK NAK message, see [FRR NAK Handler Sample](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).  
  
 The FRR orchestration is installed by default by the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup program. You need to configure the FRR system by creating a receive pipeline, receive locations, and send ports. You also need to configure FRR to specify how long it should wait for delayed NAKs, and for responses in general. For more information about FRR configuration and administration, see [Configuring FIN Response Reconciliation](../../adapters-and-accelerators/accelerator-swift/configuring-fin-response-reconciliation.md) and [Administering FIN Response Reconciliation](../../adapters-and-accelerators/accelerator-swift/administering-fin-response-reconciliation.md).  
  
 This section contains:  
  
-   [FIN Response Types](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md)  
  
-   [FRR Processing](../../adapters-and-accelerators/accelerator-swift/frr-processing.md)  
  
-   [FRR Orchestration](../../adapters-and-accelerators/accelerator-swift/frr-orchestration.md)  
  
-   [FRR Receive Location for Messages from the Back-End Application](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-the-back-end-application.md)  
  
-   [FRR Send Port for Messages to SWIFT](../../adapters-and-accelerators/accelerator-swift/frr-send-port-for-messages-to-swift.md)  
  
-   [FRR Receive Location for Messages from SWIFT](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-swift.md)  
  
-   [FRR Send Ports for Messages to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/frr-send-ports-for-messages-to-the-custom-handlers.md)  
  
-   [Handling Reconciled Message Sets](../../adapters-and-accelerators/accelerator-swift/handling-reconciled-message-sets.md)