---
title: "Resolve incomplete activity instances"
description: BAM activity instances remain active after backing up the BAMPrimaryImport database in BizTalk Server
ms.custom: ""
ms.date: "01/17/2018"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Resolve incomplete BAM activity instances - BizTalk Server
BAM stores data for incomplete activity instances in a special *active instance* table in the BAMPrimaryImport database.  
  
 If some instance records were started before the last backup of the BAMPrimaryImport database but completed after the backup, those instance records remain in an active instance table. This is because after the BAMPrimaryImport database is restored, the completion records for these instances are lost.  
  
 Although the records in the active instance table do not prevent BAM from functioning properly, we recommend that you mark these records as "completed," and then move them out of the active instance table.  
  
## Prerequisites  
Sign in as a member of the BizTalk Server Administrators group.  
  
## Create a list of incomplete ActivityIDs 
  
1.  Run the following query against the BAMPrimaryImport database:  
  
    ```  
    Select ActivityID from bam_<ActivityName>_Active where IsComplete = 0  
    ```  
  
2.  If data from external systems indicates that the activity instance is in fact completed, run the following query to manually complete the instance:  
  
    ```  
    begin transaction
    exec bam_<ActivityName>_PrimaryImport @ActivityID=N'<ActivityID>', @IsStartNew=0, @IsComplete=1  
    commit transaction
    ```  
  
> [!NOTE]
>  You can follow the same process to complete a continuation activity by replacing `ActivityID` with `ContinuationID`.  
> 
>  If the main trace has any active continuation traces, it remains active until the continuation traces are completed.  

## Remove incomplete instances
You can also remove incomplete activity instances from the BAMPrimaryImport database using a custom SQL script. See [Remove incomplete activity instances](how-to-remove-incomplete-activity-instances.md) for a sample.

## See Also  
 [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)
