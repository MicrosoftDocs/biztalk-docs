---
description: "Learn more about: Marking In-Progress Transactions as Complete in BAM"
title: "Marking In-Progress Transactions as Complete in BAM | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM, data recovery"
  - "data recovery, BAM"
  - "BAM, data loss"
  - "data loss, BAM"
ms.assetid: 8f734953-483a-481a-9ded-b48923859199
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Marking In-Progress Transactions as Complete in BAM
Business Activity Monitoring (BAM) keeps data for incomplete trace instances in a special active instance table. If some instance records were started before the last backup but completed after the backup, those records will remain in the active instance table. Although this does not prevent the system from functioning, you can manually mark these records as completed so that they can be moved out of the active instance table.  
  
 A list of incomplete ActivityIDs for a given activity can be determined by issuing the following query against the BAM Primary Import database:  
  
```  
Select ActivityID from bam_<ActivityName> where IsComplete = 0  
```  
  
 If data from external systems indicates that the activity instance is complete, you can use the following query to manually complete the instance:  
  
```  
exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
```  
  
## See Also  
 [Resolving Data Loss](../core/resolving-data-loss.md)
