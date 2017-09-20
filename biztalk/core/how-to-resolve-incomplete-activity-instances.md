---
title: "How to Resolve Incomplete Activity Instances | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instances, incomplete [BAM]"
  - "restoring, BAM"
  - "Primary Import database [BAM], incomplete instances"
  - "restoring [BAM], Primary Import database"
  - "Primary Import database [BAM], restoring"
  - "BAM, restoring"
ms.assetid: 8adbcb66-58ad-42c5-ba16-7dc07572099e
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Resolve Incomplete Activity Instances
BAM stores data for incomplete activity instances in a special *active instance* table in the BAMPrimaryImport database.  
  
 If some instance records were started before the last backup of the BAMPrimaryImport database but completed after the backup, those instance records remain in an active instance table. This is because after the BAMPrimaryImport database is restored, the completion records for these instances are lost.  
  
 Although the records in the active instance table do not prevent BAM from functioning properly, we recommend that you mark these records as "completed," and then move them out of the active instance table.  
  
## Prerequisites  
 You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.  
  
### To generate a list of incomplete ActivityIDs for an activity  
  
1.  Run the following query against the BAMPrimaryImport database:  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  If data from external systems indicates that the activity instance is in fact completed, run the following query to manually complete the instance:  
  
    ```  
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    ```  
  
> [!NOTE]
>  You can follow the same process to complete a continuation activity by replacing ActivityID with ContinuationID.  
  
> [!NOTE]
>  If the main trace has any active continuation traces, it remains active until the continuation traces are completed.  
  
## See Also  
 [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)