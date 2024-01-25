---
description: "Learn more about: Querying Activity Relationships"
title: "Querying Activity Relationships"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Querying Activity Relationships
The activity relationship information is available in a dynamically created SQL view for each activity. The name of this view is  
  
 **bam_\<** *Activity* **\>_AllRelationships**  
  
 Where \<*Activity*\> is the Name attribute of the Activity element in the BAM definition XML, which is the same as the Activity name entered using the BAM Add-in for Excel.  
  
 The relationship events occur in the context of a specific activity. For example, if the relationship between Purchase Order and Shipment occurs in the context of the Purchase Order activity, the Relationship record will show up in **bam_PurchaseOrder_AllRelationships**, but not in **bam_Shipment_AllRelationships**. For more information, see [Activity Relationships](../core/activity-relationships.md).  
  
 To find all the related activities to a purchase order you need to query both the view **bam_PurchaseOrder_AllRelationships** as well as all views **bam_\<**<em>OtherActivity</em>**\>_AllRelationships**, where \<*OtherActivity*\> is the activity in the same BAM view.  
  
 The relationship records are part of the activity instance and they are maintained in synchronization with the instance data as described in [Activity Data Storage](../core/activity-data-storage.md).  
  
## See Also  
 [Querying BAM Data](../core/querying-bam-data.md)
