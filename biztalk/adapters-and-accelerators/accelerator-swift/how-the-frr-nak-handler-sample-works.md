---
description: "Learn more about: How the FRR NAK Handler Sample Works"
title: "How the FRR NAK Handler Sample Works | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f11bd20-3a0e-4d96-8e0a-32fecc7eed7e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How the FRR NAK Handler Sample Works
The sample FRR NAK custom handler serves as an intermediary between the FIN Response Reconciliation (FRR) orchestration and the message-repair orchestration. The FRR orchestration identifies the error that occurred when the SWIFT network attempted to receive the message. The output of the FRR orchestration is a one-part message with an error object. The FRR NAK custom handler transforms that message into a two-part message, with an error part that indicates the error that occurred, enabling the message to be picked up by the message-repair orchestration. The message-repair orchestration opens the message in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form that enables you to find out what the error was, repair the message accordingly, and resubmit it so that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can resend it to SAA.  
  
 The following steps occur when the FRR NAK custom handler processes a message that the SWIFT network could not successfully receive:  
  
1.  After the FRR orchestration has correlated the failed message to the MTS21_FIN_ACKNAK NAK message, the RepairSWIFTRejectedMessage orchestration (the custom handler) picks up the original message from the MessageBox. It does so because it filters on A4SWIFT_FRRFailed==True and A4SWIFT_SendingServiceType="A4SWIFT_FrrService".  
  
2.  The custom handler does not pick up the MTS21_FIN_ACKNAK NAK message that FRR correlated to the original message. Instead, it creates an error collection object, populates it with a BRE validation error that indicates what the A4SWIFT_FRRFailedReason property was, and adds it to the original message. The message-repair orchestration can process this two-part message.  
  
3.  The custom handler promotes the following properties to cause the message to be picked up by the message-repair orchestration: A4SWIFT_Failed==True, A4SWIFT_SwiftBound==True, and BTS.Operation="A4SWIFT_DASMMarkedAsFailed". It sets the number of parts property to 2, and sets the appropriate error properties.  
  
4.  As a result of the promoted properties, the message-repair orchestration picks up the message, and the RepairSWIFTRejectedMessage orchestration terminates.
