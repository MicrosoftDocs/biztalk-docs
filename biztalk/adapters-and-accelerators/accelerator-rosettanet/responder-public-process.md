---
title: "Responder Public Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, message flow"
  - "messages, public processes"
  - "public processes, message flow"
  - "public processes, responder"
ms.assetid: 78d83954-2998-44ac-a527-5e5858c61009
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Responder Public Process
This public process on the responder receives the RosettaNet Implementation Framework (RNIF) message from the initiator, and responds accordingly.  
  
## Message Flow in the Responder Public Process  
 The message flow through the responder public process is as follows:  
  
1. The responder public process receives the RNIF message from the responder MessageBox database.  
  
2. The public process extracts the service content and headers from the action message, and sends them to the private process.  
  
   > [!NOTE]
   >  The responder public process performs standard validation on the incoming message (and any additional validation included in a validation adapter, if applicable). If validation is successful, then the public process will initiate the application adapter to perform notification in accordance with the specific implementation. The responder public process will save the message in the MessageBox database, and will notify the responder private process that it has saved the message in the MessageBox (using the `BeginNotify` method in the `ApplicationAdapter` class). For more information about the validation adapter and application adapter, see [ValidationAdapter &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md) and [ApplicationAdapter &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md).  
  
3. If the activity is asynchronous and single-action, the public process constructs an RNIF signal message (Acknowledgment Acceptance) by wrapping the service-content message part with the preamble, the service header, and (for RNIF 2.01 only) the delivery header. The public process constructs the preamble, the service header, and the delivery header using information stored in the trading partner agreement between the parties: the process configuration settings, configuration information about the source and destination parties, and the Partner Interface Process (PIP) variables. The process then sends the signal message to the initiator.  
  
   > [!NOTE]
   >  If the message is a single-action message, the message flow is complete.  
  
4. The public process enters a wait state (waiting for action by the responder private process).  
  
5. The following actions can end the wait state (waiting for action by the responder private process):  
  
   1. The responder private process returns a response service-content message and headers, in response to the original action message (that was a double-action message).  
  
       If the public process receives response service content from the private process, the public process constructs an RNIF message that contains the service content. It does so by wrapping the service-content message part with headers that contain the configuration information about the source and destination parties, and the PIP variables stored in the agreement between the parties.  
  
       The public process sends the RNIF message to the initiator using the Action/Signal Role link port.  
  
       If the public process receives notification that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] did not successfully send the message, the public process sends that status back to the private process, and then ends.  
  
       If the public process receives notification that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] successfully sent the message, the process enters a wait state (waiting for action by the initiator). This wait state is similar to the wait state that the initiator enters when it is waiting for action by the responder.  
  
   2. The public process receives a Notification of Failure message (NoF) from the initiator.  
  
   > [!NOTE]
   >  The responder private process will notify the responder public process after it has successfully processed the incoming message. Only after the responder public process has received this notification (from the `EndNotify` method in the `ApplicationAdapter` class) will the responder public process be successfully completed.  
  
6. The responder public process enters a wait state (waiting to receive a signal from the initiator in response to the response message that the responder public process sent).  
  
## See Also  
 [Public Processes](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md)   
 [Initiator Public Process](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md)   
 [ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md)   
 [ValidationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md)