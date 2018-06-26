---
title: "Identifying Lost Tracking Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data loss, HAT"
  - "reporting tools"
  - "Orchestration Debugger"
  - "Tracking database, data loss"
  - "HAT, data loss"
  - "HAT, Operation View tool"
  - "HAT, reporting tools"
  - "Operation View tool, MessageBox database"
  - "MessageBox database, Operation View tool"
  - "Operation View tool, data loss"
ms.assetid: 1ac13e2c-cd5e-437e-b924-d4547931874e
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Identifying Lost Tracking Data
You can use the BizTalk Server Administration console to help identify which tracking data has been lost as a result of a hardware failure. You can use the BizTalk Server Administration console for live or archived data.  
  
 You can use the BizTalk Server Administration console to determine which services were active at the time the MessageBox was recovered. Because there is a gap between the time that the database was recovered and the time of the hardware failure, you may not be able to determine the state of some of the transactions.  
  
 You can use tracking data to identify which service instances completed and started after the point of recovery, as follows:  
  
- Look for which instances completed or started since the last time you backed up the database.  
  
- If data in the BizTalk Tracking (BizTalkDTADb) database indicates that the message started but did not complete, and the message is not in the database, then that message was sent after the last backup.  
  
  Tracking can report on any service that completed, and it can indicate that a service started. Tracking data is first staged to the MessageBox and then moved to the BizTalk Tracking database. The data that was staged may have been lost to the backlog of the BAM Event Bus service.  
  
  While all databases need to be restored to the same mark for operational reasons, you can use a BizTalk Tracking database (that was not lost) in Archive mode to see what happened after the mark.  
  
  If tracking shows a service instance as having completed, you can terminate that instance. It may show instances that started after the point of recovery. If so, you will need to compensate for any actions these instances took and then resubmit their initial activation messages.  
  
  You can use the Orchestration Debugger to see the last shapes that executed, and then use Message Flow to see what message should have been sent or received.  
  
  If the BizTalk Tracking database was lost, all discovery of what happened past the point of recovery will need to be done by using the external systems reporting mechanisms.  
  
## See Also  
 [Resolving Data Loss](../core/resolving-data-loss.md)