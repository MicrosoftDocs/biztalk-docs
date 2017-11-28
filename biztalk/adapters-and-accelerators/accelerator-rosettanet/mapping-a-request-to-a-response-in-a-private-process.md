---
title: "Mapping a Request to a Response in a Private Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, maps"
  - "private processes, mapping requests"
  - "private processes, customizing"
  - "orchestrations, adding maps"
  - "maps, adding to orchestrations"
  - "maps, creating"
  - "customizing private processes"
  - "requests, mapping"
  - "requests, private processes"
ms.assetid: 5452c0a2-3a9b-43e7-bfa7-713eef0eab3b
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Mapping a Request to a Response in a Private Process
This topic describes how to map a request message received by the private responder process—from the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] public responder process, to a response message that can be sent to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] public responder process.  
  
 When a responder receives a request message, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] routes the request message from the public-process orchestration, to the private-process orchestration, to the line-of-business (LOB) program. The responder requires the response service content from the LOB program to generate a RosettaNet response message back to the initiator. Many of the elements in the response message are populated using the values from the request message. As a result, you can incorporate a map in the responder private-process orchestration to help the LOB program generate the response service-content message in the required format.  
  
 The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK contains the following samples that you can use when you add a map to a responder private-process:  
  
-   [3A2 Request to 3A2 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)  
  
-   [3A4 Request to 3A4 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md)  
  
-   [Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)  
  
-   [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)  
  
### To create the map  
  
1.  Start **Microsoft Visual Studio 2012**.  
  
2.  On the **File** menu, point to **Open**, and then click **Project**.  
  
3.  Locate the folder that contains the BizTalk project that contains the private-process orchestration to which you want to add the map.  
  
4.  In Solution Explorer, right-click the project, point to **Add**, and then click **New Item**.  
  
5.  In the Add New Item window, in the **Categories** pane, click **Map Files**. In the Templates pane, click **Map**. In the **Name** box, type a name for the map, and then click **Open**.  
  
6.  In the Source Schema pane, click **Open Source Schema**.  
  
7.  In the BizTalk Type Picker window, expand **Schemas**, select the PIP schema for the request message that you want to map from, and then click **OK**.  
  
8.  In the Destination Schema pane, click **Open Destination Schema**.  
  
9. In the BizTalk Type Picker window, expand **References**, expand **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, expand **Schemas**, select the PIP schema for the response message to which you want to map, and then click **OK**.  
  
10. Right-click the \<*Schema*\> node of the source schema, and then click **Expand Tree Node**.  
  
11. Repeat step 10 for the destination schema.  
  
12. In the Source Schema pane, click and hold on a field that you want to map to a field in the destination schema. Drag to the corresponding node in the Destination Schema pane.  
  
13. Repeat step 12 for all fields that you have to map between the two schemas.  
  
14. Validate and test the map. For more information, see the "Compiling and Testing Maps" topic in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.  
  
### To add the map to the orchestration  
  
1.  In Solution Explorer, double-click the private-process orchestration.  
  
    > [!NOTE]
    >  Make sure that the orchestration has references to the assemblies that contain the schemas.  
  
2.  In the Toolbox, click the **Transform** shape, and drag it to the point in the orchestration at which you have to transform the request message into the response message.  
  
    > [!NOTE]
    >  For an example of the placement of the **Transform** shape, see the PIP3A4PrivateResponder.odx orchestration. It is located in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR. This sample puts the **Transform** shape immediately under the **IsActivityDoubleAction** shape. For more information, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).  
  
    > [!NOTE]
    >  For an example of how you can incorporate multiple maps for multiple PIPs, see [Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).  
  
3.  On the orchestration design surface, click **ConstructMessage1**. In the Properties window, type a name for the shape, and a name for the message to be constructed.  
  
4.  On the orchestration design surface, click **Transform**. In the Properties window, click the ellipsis button (**...**) next to **Map Name**.  
  
5.  In the Transform Configuration window, click **Existing Map**, and in **Fully Qualified Map Name**, click the map that you just created.  
  
6.  Under **Transform**, click **Source**. Click the empty box under variable, and select the name of the request message from the drop-down list.  
  
7.  Under **Transform**, click **Destination**. Click the empty box under variable, and select the name of the response message from the drop-down list.  
  
8.  Click **OK**.  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)