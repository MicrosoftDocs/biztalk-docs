---
title: "Monitoring BizTalk Server Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7fee5015-e818-459b-aeeb-a084ef355600
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring BizTalk Server Databases
You can run the Monitor BizTalk Server SQL Agent job to identify any known issues in Management, Message Box, or DTA databases. The job is created when you configure a BizTalk group in BizTalk Server Administration console or upgrade BizTalk from the previous version.  
  
## The Monitor BizTalk Server Job  
 The Monitor BizTalk Server job scans for the following issues in Management, Message Box, and DTA databases:  
  
> [!NOTE]  
>  The Monitor BizTalk Server job only scans for issues. It does not fix the issues found.  
  
- Messages without any references  
  
- Messages without reference counts  
  
- Messages with reference count less than 0  
  
- Message references without spool rows  
  
- Message references without instances  
  
- Instance state without instances  
  
- Instance subscriptions without corresponding instances  
  
- Orphaned DTA service instances  
  
- Orphaned DTA service instance exceptions  
  
- TDDS is not running on any host instance when global tracking option is enabled  
  
  The Monitor BizTalk Server job is configured and automated to run once in a week. Since the job is computationally intensive, we recommended that you schedule it to run during periods of downtime or low traffic.  
  The job fails if it encounters any issues; the error string returned contains the number of issues found. Else, it runs successfully. You can see the details in the job history. If you run the job with Administrator privileges, the error string will be logged to both the job history and the SQL Server Application log.  
  
> [!IMPORTANT]  
>  Failure of this job does not necessarily constitute a critical issue, but rather an issue that should be investigated and addressed as part of regular maintenance of the BizTalk Server databases. This job fails by design in the event it discovers one of the issues listed above.