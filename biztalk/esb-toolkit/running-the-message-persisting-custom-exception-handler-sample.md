---
description: "Learn more about: Running the Message Persisting Custom Exception Handler Sample"
title: "Running the Message Persisting Custom Exception Handler Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0a4c819-f6bd-4dea-8be9-e3006337665f
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running the Message Persisting Custom Exception Handler Sample
The Message Persisting Custom Exception Handler sample demonstrates a loosely coupled, generic handler that receives fault messages, extracts the Microsoft BizTalk messages they contain, and writes them as disk files to the file system.  
  
 The sample shows how you can use a custom exception handler in an orchestration. When a process in the orchestration (EAIProcess.odx) encounters an error, the exception handler generates and publishes an ESB fault message. This fault message includes in its payload the messages (including their BizTalk-related context properties) that were "in flight" when the exception occurred, as well as the current System.Exception instance caught by the BizTalk Orchestration engine. When this occurs, a "Denied" message and an "Approved" message are persisted with the fault message.  
  
 A second orchestration named EAIGenericHandler.odx, which is deployed in a decoupled manner and acts as a custom exception handler, subscribes to the specific fault code generated in the EAIGenericHandler.odx orchestration and consumes the fault message. This exception handler extracts the original messages (as type-less documents) and the System.Exception instances originally persisted in the fault message.  
  
 The Message Persisting Custom Exception Handler sample differs from the Repair and Resubmit Custom Exception Handler sample in that the EAIGenericHandler.odx orchestration used in this sample does not have a dependency on the schemas used in the fault publishing orchestration process (EAIProcess.odx). Specifically, the EAIGenericHandler.odx orchestration retrieves the original messages from the fault message as System.Xml.XmlDocument instances instead of typed messages based on the schemas used in the EAIProcess.odx orchestration. It also returns the messages as a collection that code can easily enumerate.  
  
 The custom exception handler (EAIGenericHandler.odx) then writes both the "Denied" and the "Approved" messages to the file system location \Source\Samples\Exception Handling\Test\Filedrop\EAIGenericHandler.PostTmpMsg.  
  
 Additionally, there is a generic send port named ALL.Exceptions_FILE configured to use the GlobalFaultProcessor pipeline installed as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Exception Management Framework. This port subscribes to all exceptions in the system, both BizTalk failed message routing messages and ESB fault messages. The Exception Management Framework normalizes them all to a single format and serializes them using a Microsoft InfoPath processing instruction to the location \Source\Samples\Exception Handling\Test\Filedrop\All_Exceptions.  
  
## Installation  
 All the exception management samples use the same set of core services and BizTalk application artifacts. Therefore, you have to install the exception management sample artifacts only once to be able to run all the exception management samples. For information about how to install the exception management samples, see [Installing the Exception Management Samples](../esb-toolkit/installing-the-exception-management-samples.md).  
  
## Running the Sample Application  
 **To run the Message Persisting Custom Exception Handler sample**  
  
1.  Before you run this sample for the first time, make sure that the receive location and send port URL point to the appropriate directories in the \Source\Samples\Exception Handling\Test\Filedrop folder. The receive location should specify the folder EAIProcess.RequestPort, and the send port URL should specify the folder EAIGenericHandler.PostTmpMsg.  
  
2.  If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.  
  
3.  Start the sample by copying the sample file named Request_EAIGenericHandler.xml, located in the \Source\Samples\Exception Handling\Test\Data folder, to the folder specified for the EAIProcess.RequestPort_FILE receive location: \Source\Samples\Exception Handling\Test\Filedrop\EAIProcess.RequestPort.  
  
4.  Open the folder named EAIGenericHandler.PostTmpMsg (in the \Source\Samples\Exception Handling\Test\Filedrop\ folder). You will see the original message.  
  
## How the Sample Works  
 The message you submit activates the EAIProcess orchestration. When the EAIProcess orchestration processes the message, it attempts to divide 1 by the unit price. Because the unit price is zero, a divide-by-zero exception occurs. Code in the event handler of the orchestration catches this exception and creates a fault message. The order quantity in the message is less than 10, so the business logic dictates that this exception has a **FaultCode** field value of **2000**.  
  
 The EAIProcess orchestration then publishes the fault message to the BizTalk Message Box through a direct-bound port, and the orchestration ends.  
  
 A custom fault handler orchestration named EAIGenericHandler, which subscribes to messages with a **FaultCode** field value of **2000**, picks up the new fault message. The code in the orchestration extracts all the messages from the exception (fault) message and writes them to disk files.
