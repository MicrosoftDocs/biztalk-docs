---
title: "Activity and ActivityID Nodes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ActivityID nodes [Tracking Profile Editor]"
  - "Activity nodes [Tracking Profile Editor]"
  - "Tracking Profile Editor, node descriptions"
  - "activities [BAM], definitions"
ms.assetid: 94d4130a-53c5-4cd5-916a-4a6bd9acbf23
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Activity and ActivityID Nodes
Activity and ActivityID nodes are used to contain and identify an activity definition. The Activity node is the parent folder for the items in the activity definition. All data items and business event nodes are subordinate to and contained within the associated activity node. The name of the Activity node should reflect the name of the activity itself.  
  
 The ActivityID node is an automatically generated item in the activity definition and is intended to hold a unique identifier for the activity. The ActivityID node can be used to track user supplied identifiers or identifiers that are system generated. For example, in a scenario in which you have purchase order number as a unique identifier across all purchase orders in the system, you can use it as the ActivityID, in which case you will map the value of the ActivityID from some event source, such as the PO number field in the purchase order schema. On the other hand, if the purchase order value is not unique, then you can leave the node unmapped, and BAM will automatically generate unique identifiers at run-time.  
  
 Activities can be related to other activities. In some scenarios these relationships are explicitly part of the observation model.  Specifically, when any user view includes two or more activities, there is an automatic relationship between those activities.  When such a relationship exists, a relationship node is automatically created in the activity tree, under the Activity node, for each known peer activity. In scenarios where there  is a data relationship and no spanning view exists, you can manually add a relationship node to  the activity tree.  
  
 In either case, the purpose of the relationship node is to provide an identifier for the related activity. For example, purchase orders and shipments can have a many-to-many relationship (one PO is fulfilled by multiple shipments; one shipment can carry a product satisfying many POs).  The activity record for each purchase order can have multiple pointers to related shipments, and each shipment activity record could point to one or more Purchase Orders.  In database terms, the value of the relationship node is the foreign key into the table for the other activity.  
  
## Working with Activity ID nodes  
 For example, consider the following scenario: the EquityLoan orchestration contains the activity folder LoanProcess. It references business events including the following:  
  
- LoanApplicationReceived  
  
- CHRequest  
  
- CHResponse  
  
- AppraisalRequest  
  
- AppraisalResponse  
  
- Approved  
  
- Denied  
  
  The ActivityID node enables the solution developer to extract data that uniquely identifies the activity, such as a purchase order number, or, in the case of the sample scenario, the SSN field of the message. If you do not drag any data to the ActivityID node, an automatically generated GUID identifies the business activities.  
  
  To define the relationship between business events or milestones in different orchestrations, the target orchestration must reference the ActivityID. For more information about how to implement relationships using TPE, see [Relationship Nodes](../core/relationship-nodes.md).  
  
## See Also  
 [TPE Activity View Nodes](../core/tpe-activity-view-nodes.md)