---
title: "Initiator Public Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "public processes, initiator"
  - "CIDX, 0A1 messages"
  - "messages, 0A1 messages"
  - "messages, message flow"
  - "messages, public processes"
  - "0A1 messages"
  - "public processes, message flow"
ms.assetid: 371d0792-d346-405b-a8f4-2dfa64dd1566
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Initiator Public Process
This process initiates RosettaNet Implementation Framework (RNIF) messaging on the initiator system by creating and sending the initial RNIF business message.  
  
## Message Flow in the Initiator Public Process  
 The message flow through the initiator public process is as follows:  
  
1. The initiator public process receives the service content and attachments from the private process through the service-content port.  
  
2. The public process sends the response to the private process, and does no further processing.  
  
3. If the public process receives notification that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] did not successfully send the message, the public process sends that status back to the initiator private process, and then ends.  
  
4. If the public process receives notification that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] successfully sent the message, the process enters a wait state (waiting for action by the responder).  
  
5. The following actions can end the wait state:  
  
   1.  The public process receives an acknowledgement signal from the responder.  
  
        If non-repudiation for the signal is required (as set in the process configuration settings), the process reads the digest, correlates the digest in the signal with the digest in the original action message, and then persists the signal.  
  
        The public process sends the headers and service content of the signal to the private process.  
  
   2.  The public process receives a double-action response message from the responder.  
  
        The process extracts the service content and headers from the response message, and sends them to the private process.  
  
        If the activity is synchronous, the process constructs an RNIF signal message by wrapping the service-content message part with the preamble, service header, and delivery header (for RNIF 2.01). The process creates the preamble and headers using configuration information about the source and destination parties, and the PIP variables stored in the trading partner agreement between the parties. The process then sends the signal message to the responder.  
  
        If the activity is asynchronous, the process ends.  
  
   3.  The public process receives a Notification of Failure (NoF) message from the responder. The public process sends a corresponding status message to the initiator private process. The private process then handles the error and ends both processes.  
  
   4.  The public process does not receive an acknowledgement signal from the responder within the Time to Acknowledge period (as set in the process configuration settings). If so, one of the following occurs:  
  
        If the number of retries (as set in the process configuration settings) has not reached zero, and the activity is asynchronous, the public process sends the message again.  
  
        If the number of retries (as set in the process configuration settings) has not reached zero, and the activity is synchronous, the public process initiates a 0A1 message.  
  
       > [!NOTE]
       >  CIDX does not support 0A1 messages.  
  
        If the number of retries reaches zero without a successful send, the public process posts an error message, and if this is not CIDX, the public process sends a 0A1 message.  
  
        If the activity is synchronous, and this is not CIDX, the public process initiates a 0A1 message.  
  
   5.  If no action occurs within the Time to Perform period, and this is not CIDX, the public process sends a 0A1 message.  
  
## See Also  
 [Public Processes](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md)   
 [Responder Public Process](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)