---
title: "Running Orchestrations3 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, running"
  - "Receive shape [Orchestration Designer], starting orchestrations"
  - "Start Orchestration shape [Orchestration Designer], starting orchestrations"
  - "Call Orchestration shape [Orchestration Designer], starting orchestrations"
  - "Receive shape [Orchestration Designer], activating orchestrations"
ms.assetid: 5bfe61c9-80e0-4a0a-b6b1-ab48037e665e
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running Orchestrations
Orchestration instances are designed to be triggered either by an explicit call from another orchestration—using a **Call Orchestration** shape or **Start Orchestration** shape—or by receipt of an activation message. The activation message schema is specified in the **Message** property. You should design your orchestration accordingly, and either set the **Activate** property on a **Receive** shape to true, or make sure that a calling orchestration exists and is configured properly to run the new orchestration.  
  
 Before any instances can run, you must first bind and deploy the BizTalk assembly, and then enlist and start the orchestration engine to begin processing. For more information, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md) and [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md). When an orchestration is invoked from another orchestration, or a message is presented to the engine that matches the criteria in an activation receive, the engine creates a new instance of the orchestration and runs that instance. It can run many different instances concurrently.  
  
## Calling and starting orchestrations  
 The **Call Orchestration** shape and **Start Orchestration** shape can be used to activate another orchestration. In both cases, the caller can pass in parameters to exchange information with the other orchestration. For more information, see [How to Add Parameters to Orchestrations](../core/how-to-add-parameters-to-orchestrations.md).  
  
## Using activation receives with filter expression  
 The **Receive** shape might also use a filter expression to require further criteria for activation. If the message is of the correct type and some property or properties of the message meet all of the criteria in the filter expression, the **Receive** shape accepts the message and the orchestration is activated. Such a Receive shape is referred to as an *activation receive*.  
  
## See Also  
 [How to Configure the Call Orchestration Shape](../core/how-to-configure-the-call-orchestration-shape.md)   
 [How to Configure the Start Orchestration Shape](../core/how-to-configure-the-start-orchestration-shape.md)   
 [How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md)   
 [Building and Running Orchestrations](../core/building-and-running-orchestrations.md)