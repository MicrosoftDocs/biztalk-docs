---
title: "Best Practices for Maintaining BizTalk Server Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93333f41-ee83-4b64-b381-66584a7d5551
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Maintaining BizTalk Server Databases
This topic lists some best practices for maintaining [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
- Make sure the SQL Server Agent is running on the SQL Server. When the SQL Server Agent is stopped, the built-in BizTalk SQL Server Agent jobs that are responsible for database maintenance cannot run. This behavior causes database growth, and this growth may cause performance issues. For information about monitoring SQL Server Agent Jobs see [Monitoring SQL Server Agent Jobs](../technical-guides/monitoring-sql-server-agent-jobs.md).  
  
- Make sure the SQL Server LDF and MDF files are on separate drives. Having the LDF and MDF files for the BizTalkMsgBoxDb and BizTalkDTADb databases on the same drive may result in disk contention.  
  
- Do not enable message body tracking, if not required. Frequently, you may want to enable message body tracking while you develop and troubleshoot a solution. If so, make sure you disable message body tracking when you are done. If you keep message body tracking enabled, the BizTalk Server databases grow. If you have a business need that requires you to enable message body tracking, confirm that the **TrackedMessages_Copy_BizTalkMsgBoxDb** and **DTA Purge and Archive** SQL Server Agent jobs are running successfully.  
  
- Typically, smaller transaction logs cause better performance. To keep the transaction logs smaller, configure the **Backup BizTalk Server** SQL Server Agent job to run more frequently. For more information, see the [BizTalk Server Database Optimization white paper](http://go.microsoft.com/fwlink/?LinkId=153594) (http://go.microsoft.com/fwlink/?LinkId=153594).  
  
- Use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Best Practices Analyzer (BPA) to evaluate an existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment. The BPA performs numerous database-related checks. You can download the BizTalk Server Best Practices Analyzer tool from [BizTalk Server Best Practices Analyzer tool](http://go.microsoft.com/fwlink/?LinkId=83317) (<http://go.microsoft.com/fwlink/?LinkId=83317>).  
  
## See Also  
 [Checklist: Maintaining and Troubleshooting BizTalk Server Databases](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)   
 [Large-growing BizTalk Server Database Tables](../technical-guides/large-growing-biztalk-server-database-tables.md)