---
title: "Creating a Custom Handler for Rejected Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "custom handlers"
  - "Message Repair and New Submission, rejected messages"
  - "Message Repair and New Submission, custom handlers"
ms.assetid: 28d74504-6c62-427a-b75d-456fbe43ec3a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a Custom Handler for Rejected Messages
If you reject a message in the verification or approval stage, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] returns the message to the first stage defined for the workflow (which in this case is always repair, even if Create is the first stage in the workflow). However, if the first stage of the workflow rejects the message, the repair orchestration publishes the message to the MessageBox with promoted properties indicating that the MrsrRepair orchestration rejected the message. To handle these messages, you can create a custom handler (orchestration) that subscribes to these promoted properties and processes the messages as required.  
  
 A message can fail in the MrsrRepair orchestration for multiple reasons. When it does, the orchestration promotes the properties in the following table, and assigns these properties the value, or one of the values, shown in the right column of the table.  
  
|Property|Values|  
|--------------|------------|  
|BTS.Operation|A4SWIFT_MRSRFailed|  
|A4SWIFT_MRSRFailedReason|Timeout<br /><br /> Rejected (means the message has been rejected from the first stage)<br /><br /> CantRepairInInfoPath|  
|A4SWIFT_MRSRLastStage|\<name of last stage (role) that the message was in before failing\>|  
|A4SWIFT_MRSRDepartment|\<name of department\>|