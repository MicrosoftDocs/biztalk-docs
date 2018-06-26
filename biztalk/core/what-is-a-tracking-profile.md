---
title: "What Is a Tracking Profile? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tracking profiles, about tracking profiles"
  - "tracking profiles, Tracking Profile Editor"
  - "Tracking Profile Editor, tracking profiles"
  - "tracking profiles"
ms.assetid: b579bdc4-7c69-4fa0-bbc1-f98170c13d4f
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is a Tracking Profile?
A profile is a set of characteristics that define a business process. A tracking profile contains the mapping of these characteristics from an activity to orchestrations and ports. A tracking profile is a file with a .btt file name extension.  
  
## Using tracking profiles in the TPE  
 Users of the TPE create a map, or tracking profile, between items in a BAM activity and the BizTalk Server solution sources for those items. BAM activities consist of the milestones and contextual data that make up the "visibility wish-list" and define a unit of work in the business that the tracking profile follows. For more information about activities, see [Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md).  
  
 When you create a tracking profile using the TPE, you are working with the following objects:  
  
- BAM activities  
  
- BizTalk orchestrations in deployed assemblies  
  
- Receive and send ports  
  
- Message schemas in deployed assemblies  
  
- Context properties  
  
- BAM Primary Import database  
  
- BizTalk Management database  
  
- BizTalk Tracking database  
  
  You define the data extraction from an orchestration by dropping items from message schemas, orchestration shapes, and context properties into business milestone (event) and data item folders.  
  
  For example, consider a BAM activity that includes a milestone called PO Received and has a Messaging port through which purchase orders flow to initiate processing. Developers can associate the `PO Received` milestone with a BizTalk Messaging property called `PortEndTime` for the port in their solution. Semantically, this indicates that the PO is successfully received once the receive port concludes its action and populates the `PortEndTime` property. The developer makes this and any other mappings to complete the tracking profile. All items in the activity are mapped if they have a BizTalk Server source, or are left unmapped to be populated by API calls directly if the source of the data or event is from a process outside of BizTalk Server’s run-time environment.  
  
  Although each pane or view in the TPE has a unique function, all the views and folders have similar navigational features to help you find and manipulate information.  
  
## Who uses tracking profiles and the TPE?  
 Users involved with enterprise integration development use tracking profiles and the TPE to map BizTalk Server event sources to BAM target activities. The resulting .btt file is handed off to IT Implementation for deployment.  
  
 IT Implementation users will typically apply tracking profiles using command-line tools (BTTDeploy). The IT user can also use the TPE directly to apply the tracking profile.  
  
 Users in IT Operations may be responsible for periodic updates to tracking profiles on a scheduled basis (including any database operations required, such as backup and restore), especially as a result of changes in business requirements.  
  
## See Also  
 [Tracking Profile Editor](../core/tracking-profile-editor.md)