---
title: "Defining a Custom BAM View for Message Repair and New Submission Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM views"
  - "Message Repair and New Submission, BAM views"
ms.assetid: 76a6e78d-9b11-4b43-a500-a9d7666ee468
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Defining a Custom BAM View for Message Repair and New Submission Data
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Setup provides a BAM definition file that defines a business activity and a business view. You can deploy the BAM definition file to use that view, or you can create a custom view that you can add to the BAM definition file.  
  
 The BAM definition file is MrsrActivities.xml in *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\BAMTracking. It defines a Message activity and a RepairView view. For more information about deploying MrsrActivities.xml by using the bm deploy utility, see [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.  
  
 Create the custom view in the Business Activity Monitoring View Wizard from the BAM workbook. For more information about creating a custom view, see "Creating a BAM View" in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Information Worker Help.  
  
 The Message activity in MrsrActivities.xml includes the following items that you can add to the custom view:  
  
> [!NOTE]
>  When durations are calculated in BAM, they are measured in units of one day (14.4 minutes = .01 day).  
  
|Item|Use|Item type|  
|----------|---------|---------------|  
|Destination BIC|The LT address of the receiver of the message (taken from Application Header Block Input for messages to SWIFT, or from Block 1 for messages from SWIFT where the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] institution is the destination).<br /><br /> This data is always present (from Application Header Input Destination LT for SWIFTBound messages, or from Basic Header LT for messages received from SWIFT).|Business Data - Text|  
|End Time|The date and time when the MRSRRepair orchestration completed processing the message (MRSR_Completed or MRSR_Failed).<br /><br /> This data is present only for messages that have completed MRSR workflow, that is, have exited with **BTS.Operation** == **A4SWIFT_MRSRCompleted** or **A4SWIFT_MRSRFailed**.|Business Milestone|  
|Reference|The unique reference identifier for this message or transaction as assigned by the sending institution; taken from field 20 or 20C(SEME)|Business Data - Text|  
|Message Type|The type of FIN or GPA message.<br /><br /> This data is always present (Application Header Input or Application Header Output).|Business Data - Text|  
|New Submission|An indicator as to whether this is a new entry (Y) or a message that originated from another system or SWIFT (N).<br /><br /> This data is present only for messages that were originated by role with Create capability.|Business Data - Text|  
|Priority|The priority of the SWIFT message (N = normal, U = urgent, S = system).<br /><br /> This data is always present.|Business Data - Text|  
|Received Time|The date and time when the MRSRRepair orchestration last received the message (from the previous stage – see Stage below).<br /><br /> This data is always present.|Business Milestone|  
|Sender BIC|The LT address of the originator of the message (taken from Block 1 for messages to SWIFT where the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] institution is the sender, or from Application Header Output for messages from SWIFT).<br /><br /> This data is always present (from Basic Header LT Address for SWIFTBound Messages, or from Application Header Output for messages received from SWIFT).|Business Data - Text|  
|Send Time|The date and time when the MRSRRepair orchestration last sent the message to MRSR site (for the current stage).<br /><br /> This data is always present unless the message is in process in the orchestration.|Business Milestone|  
|Start Time|The date and time when the MRSRRepair orchestration initially received the message either as a new submission or as a message from an interface (internal system or SWIFT).<br /><br /> This data is always present.|Business Milestone|  
|Last Stage|The last completed step in the workflow (always the stage before where the message is now)|Business Data - Text|  
|Status|Can be:<br /><br /> -   Completed (if successful)<br />-   Reset and reason (for workflow reset if the workflow restarted)<br />-   Failed and reason (if message completed unsuccessfully, that is, was rejected or timed out).<br /><br /> This data is always present.|Business Data - Text|  
|Department|The department selected by the MRSRRepair orchestration according to the Department Policy (dependent on the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] institution)|Business Data - Text|  
|Username|The name of the user associated with the previous stage (see Stage above)|Business Data - Text|  
|Current Stage|The workflow step to which the MRSRRepair orchestration has delivered the message (for example, the Inbox).<br /><br /> This data is present unless the message has completed message repair.|Business Data - Text|