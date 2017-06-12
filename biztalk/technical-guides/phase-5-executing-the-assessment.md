---
title: "Phase 5: Executing the Assessment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d40fc64-b6cb-448b-8ea1-a6ad7302ab8b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Phase 5: Executing the Assessment
The Execute phase is where the performance data is generated through automated load testing and where performance bottlenecks are discovered and addressed. This phase has an iterative process whereby performance bottlenecks are reduced or eliminated by testing, evaluating performance, optimizing, and testing again.  
  
 This topic describes the steps that are typically followed during the Execute phase of a BizTalk Server performance assessment:  
  
## Step 1: Run automated tests  
 Begin the Execute phase by running automated tests. A BizTalk Server performance assessment typically focuses on throughput and/or latency testing but may include build verification and functional tests. For comprehensive information about running automated testing, see [Implementing Automated Testing](../technical-guides/implementing-automated-testing.md).  
  
## Step 2: Document and evaluate test results  
 At the conclusion of each test, thoroughly document the test results and evaluate whether the stated performance goals have been met.  
  
## Step 3: Modify the configuration of BizTalk Server, third-party systems, or solution artifacts to tune for performance based on the test results  
 Use the test results to make decisions about how to optimize the environment to reach stated throughput or latency goals.  
  
## Step 4: Record all changes made to the environment  
 Ensure that any changes made to the environment are thoroughly documented. A record of the changes will allow you to easily apply the changes in the production environment and will accommodate the undoing of changes if need be.  
  
## Step 5: Repeat this cycle until goals are achieved  
 Continue the cycle of testing, evaluating and documenting results, optimizing the environment, and documenting changes to the environment until the desired performance goals are reached.  
  
## Step 6: Summarize test results at the end of each day  
 Complete an “executive summary” of the test results and progress made at the end of each day. Compile an e-mail that contains the summary, and send to all stakeholders in the performance assessment to keep everyone informed of progress that is being made.  
  
## Step 7: Update the project plan as timeline goals are met  
 The timeline developed in the Plan phase is a good reference for the overall progress of the performance assessment. Update this timeline as necessary to communicate the progress to all stakeholders.  
  
## See Also  
 [Phases of a Performance Assessment](../technical-guides/phases-of-a-performance-assessment.md)