---
title: "3A4 Private Responder Orchestration Using a Business Rule | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33d87952-def6-4202-b535-3d80171332eb
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# 3A4 Private Responder Orchestration Using a Business Rule
The PIP3A4PrivateResponder.odx sample is a private-process orchestration that demonstrates how to implement a Partner Interface Process (PIP)-specific responder private process incorporating a business rule. For more information about this process, see [Defining a Business Rule for a Private Process Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/defining-a-business-rule-for-a-private-process-orchestration.md).  
  
 By default, the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Setup program installs the sample in \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\PipAutomation\3A4.  
  
## Procedures  
  
#### To build and initialize this sample  
  
1.  At a command prompt, locate the *\<drive>*:\Program Files\ Microsoft BizTalk Accelerator for RosettaNet \<version>\SDK\PIPAutomation\3A4 folder.  
  
2.  Run the file Setup.bat, which uses the Binding.xml binding file to perform the following actions:  
  
    -   Compiles the Helper project and registers the assembly in the global assembly cache.  
  
    -   Compiles the PIP3APrivateResponder project and registers the assembly in the global assembly cache.  
  
    -   Creates the LOB_To_PrivateResponder receive port.  
  
    -   Creates the LOB_To_PrivateResponder receive location.  
  
    -   Creates and starts the PrivateResponder_To_LOB send port.  
  
    -   Compiles and deploys the PIP3A4PrivateResponderProcess orchestration.  
  
    > [!NOTE]
    >  You must complete the port binding configuration of the PIP3A4PrivateResponderProcess orchestration using BizTalk Explorer.  
  
    > [!NOTE]
    >  To undo changes made by setup.bat, manually unenlist the PIP3A4PrivateResponder.odx orchestration, undeploy the Helper and PIP3A4PrivateResponder assemblies, and undeploy and then delete the samplebtarnpolicy rules policy. You cannot use Cleanup.bat in the *\<drive>*:\Program Files\ Microsoft BizTalk Accelerator for RosettaNet \<version>\SDK\PIPAutomation\3A4 folder to undo changes made by setup.bat.  
  
## Demonstrates  
 This sample subscribes 3A4 request action and signal messages. It works in both 3A4 synchronous and asynchronous processes. All other PIP messages still route through the generic [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] private process. This sample invokes the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Business Rule Engine, and passes to the Rule Engine the incoming 3A4 request message.  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] provides a sample business-rule policy named samplebtarnpolicy.xml in \<*drive*>:\Program Files\ Microsoft BizTalk Accelerator for RosettaNet \<version>\SDK\PipAutomation\3A4. For more information, see [Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md).  
  
 To work with the sample, set up a business rule. If the message meets the business rule, then the process saves the incoming action message in the MessagesToLOB table, setting the Delivered Status to 2. The Delivered column value must be nonzero, so that the line-of-business application knows that it does not have to generate a confirmation for this request. The process then maps the 3A4 request message to a 3A4 confirmation message, and submits the response to the MessageStorageIn table using the `SubmitRNIF` method.  
  
 If the message does not meet the business rule, the process saves the incoming action message in the MessageStorageOut table, and sets Delivered Status to 0.  
  
 This sample includes a binding file (Binding.xml) that you can use to set up a send port (PrivateResponder_To_LOB), a receive port (LOB_To_PrivateResponder), and a receive location (LOB_To_PrivateResponder) for use with the PIP3A4PrivateResponder.odx orchestration. Use the BTSTask command to import the bindings in the Binding.xml file. For more information, see the "ImportBindings Command" topic in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.  
  
## See Also  
 [Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)   
 [Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)   
 [Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)