---
title: "Using the TPE | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking Profile Editor, about Tracking Profile Editor"
  - "tracking profiles, prerequisites"
ms.assetid: ebe9a5da-66ec-482d-8aac-892a829ca996
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the TPE
You use the Tracking Profile Editor (TPE) to map orchestrations and properties to BAM activity definitions.  
  
 Users of the TPE create a map, or tracking profile, between items in a BAM activity such as milestones and contextual data (sometimes called the "visibility wish-list") and the BizTalk solution sources for those items.  
  
 **Creating a Tracking Profile**  
  
 For example, consider a BAM activity that includes a milestone called “PO Received.” The developer knows, from having created processes in other BizTalk Server development tools, that the actual process includes a messaging port through which purchase orders flow to initiate processing. The developer determines that the activity milestone, called “PO Received,” is most correctly associated with a BizTalk messaging property called “PortEndTime” for the port in the solution. The developer makes this and any other mappings to complete the tracking profile by loading the activity, selecting event sources, and dragging the appropriate items from the event source and dropping them on the corresponding nodes in the activity tree definition.  
  
 **Prerequisites for Creating a Profile**  
  
 There are two prerequisites for creating a tracking profile:  
  
1. A BAM activity has been defined by the business analyst, as part of an overall observation model, and has been deployed by the system administrator.  
  
2. A BizTalk solution (including orchestrations, schemas, map, and pipelines) has been successfully deployed in the target environment.  
  
   These prerequisites are necessary since after installation the TPE is not populated with any data to retrieve from the databases.  
  
   **Creating a Profile for Customized BAM Solutions**  
  
   Tracking profiles are only relevant to run-times that have an interceptor. For BAM solutions that consist of custom code using the BAM APIs, there is no associated BAM run-time interceptor, and sending data to BAM can be done in only one of two ways:  
  
- Directly through the BAM APIs. Using the APIs developers can explicitly send event data to the BAM infrastructure. For more information about using the BAM APIs, see [Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md).  
  
- Indirectly, through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] properties. In the case where the custom code is executing inside some run-time context that does have an associated interception technology, such as a custom pipeline - or expression/action shapes in invoking a custom assembly, You can use the BAM APIs as noted above or use traditional data promotion techniques. By promoting the properties you make them accessible to the TPE and the association of that event data to a BAM activity item can then be made in the TPE using the correct context property. For more information about promoting properties, see [Promoting Properties](../core/promoting-properties.md).  
  
## In This Section  
  
-   [Creating Tracking Profiles](../core/creating-tracking-profiles.md)  
  
-   [How to Remove Orphaned Tracking Profiles](../core/how-to-remove-orphaned-tracking-profiles.md)  
  
-   [Using Multiple Continuations](../core/using-multiple-continuations.md)