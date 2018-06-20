---
title: "HubScenario Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb6990ec-aea2-4362-8573-7f737a4fc7f1
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HubScenario Sample
The HubScenario sample demonstrates how to manage message transmission in a hub scenario. It transforms a message sent to an intermediary hub into a message to be sent to the final recipient.  
  
 HubScenario extracts the DUNS number of the final recipient from the service content. It manages signing and encryption certificates, and the destination URL. It generates a new message for the final recipient.  
  
 This sample handles 3A4 request and response messages, and 0C1 request messages. When you use HubScenario to create an application for your purposes, you will have to generate routines for each message Partner Interface Process (PIP).  
  
 The HubScenario sample includes HubHelper.cs and HubScenario.odx projects.  
  
 The HubScenario sample also includes a binding file that you can use to import bindings for a receive port (MessagesToLOB_Receive_Port) and receive location (MessagesToLOB_Receive_Location) for use with the HubScenario.odx orchestration. This binding file (HubScenarioBinding.xml) is located in *\<drive\>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version\> Accelerator for RosettaNet \SDK\HubScenario. Use the BTSTask command to import the bindings. For more information, see the "ImportBindings Command" topic in BizTalk Server Help.  
  
### To build and initialize this sample  
  
1. In Visual Studio, open \<drive\>:\Program Files\Microsoft Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\HubScenario\HubScenario.btproj. In Solution Explorer, right-click the HubScenario project, and then click Properties. In the Properties page for the HubScenario project, in the Signing tab select **Sign the assembly** checkbox, and select **HubScenario.snk** in **Choose a strong name key file** and click **Ok**.  
  
2. In Solution Explorer, right-click the HubHelper project, and then click Properties. In the Properties page for the HubHelper project, in the Signing tab check Sign the assembly checkbox. In Choose a strong name key file field, select new type **HubHelper.snk** as Key file name and click **OK**.  
  
   > [!NOTE]
   >  If you do not manually enter the assembly key file in the HubScenario and HubHelper projects, the assemblies will not deploy.  
  
3. At a command prompt, move to *\<drive\>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\HubScenario folder. Run the file Setup.bat (or on a 64-bit computer, run Setupx64.bat).  
  
## Demonstrates  
 The HubScenario.ods orchestration demonstrates how to perform the following tasks:  
  
1. Receives the message from the line-of-business application.  
  
2. Removes the `CDATA` element from the service content, returning the XML string.  
  
3. Retrieves the destination party name, PIPCode, PIPInstanceID, and PIPVersion for the final message.  
  
4. Retrieves the DUNS number for the final recipient.  
  
5. Determines the category of the message, and adds the DOCTYPE element that contains a reference to the appropriate schema to the service content.  
  
6. Constructs a message with the new destination party name, DUNS number, PIP code information, and service content.  
  
7. Submits the message for processing by [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. This is a call to `SubmitRNIF.SubmitMessage`.  
  
## See Also  
 [Sample Hub-Based Scenario](../../adapters-and-accelerators/accelerator-rosettanet/sample-hub-based-scenario.md)   
 [Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)