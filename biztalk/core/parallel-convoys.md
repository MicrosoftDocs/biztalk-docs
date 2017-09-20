---
title: "Parallel Convoys | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Parallel Task shape [Orchestration Designer], concurrent receive tasks"
  - "messages, convoys"
  - "correlation sets, concurrent receive tasks"
  - "correlation sets, Parallel Task shape [Orchestration Designer]"
  - "orchestrations, messages"
  - "messages, correlating to orchestrations"
ms.assetid: 036aa8c0-f49c-47f0-ac1e-6c667bca3811
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Parallel Convoys
A parallel convoy enables multiple single messages to join together to achieve a required result. The set of related messages can arrive in any order, but BizTalk Server must receive all of them before starting the process.  
  
 For example, when a hospital admits a new patient, the hospital requires several pieces of information from the patient, including insurance information, past medical history, and contact information. Several different people collect this information, including an insurance specialist, a nurse, and a receptionist. Several different systems process this information. The order in which collection and submission of this information occurs is not guaranteed. For example, information collectors may be busy with other patients, the medical records department may be behind in their schedule, or the insurance system may not be functioning correctly. Assembling this information for the patient in an organized manner must occur throughout the time the patient spends at the hospital. This guarantees that the patient receives appropriate care and accurate billing.  
  
 The preceding scenario is an example of a business scenario that requires parallel convoy message processing. The business requirements dictate the receipt of three different types of messages before admitting the patient into the hospital. These three messages are the Insurance, History, and Patient messages. Any one of these messages can be the first message to arrive for the patient, and this creates a race condition. To resolve this issue, three **Receive** shapes are put into a **Parallel Actions** shape and each receive is marked as Activate = True. This enables any one of the three messages to start the orchestration. The orchestration instance waits until the other two messages arrive before proceeding to further processing.  
  
## Implementing Parallel Convoys  
 You can implement parallel convoys by using the "parallel correlated receives" messaging design pattern in BizTalk Server. Parallel correlated receives are correlated receive statements in two or more branches of a **Parallel Actions** shape. If a correlation is initialized in more than one parallel task, each correlated receive must initialize exactly the same set of correlations. The first such task that receives a correlated message performs the actual initialization, and validation is performed on the other tasks in the **Parallel Actions** shape in orchestration.  
  
 For an example of parallel convoy implementation, see the SDK sample "Parallel Convoy" at [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## See Also  
 [Working with Convoy Scenarios](../core/working-with-convoy-scenarios.md)   
 [Sequential Convoys](../core/sequential-convoys.md)