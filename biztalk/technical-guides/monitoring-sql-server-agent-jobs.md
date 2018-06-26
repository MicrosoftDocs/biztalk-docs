---
title: "Monitoring SQL Server Agent Jobs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60d0a377-c86d-429b-9e48-c37bd5b0f912
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring SQL Server Agent Jobs
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes multiple SQL Server Agent jobs that perform important functions to keep your servers operational and healthy. You should monitor the health of these jobs and ensure that they are running without errors.  

## Guidelines for Monitoring the SQL Server Agent Jobs  
 Following are guidelines for monitoring the jobs:  

- **Verify that the SQL Server Agent service is running**  

- **Verify that the SQL Server Agent jobs installed by BizTalk Server are enabled and running successfully**  

   The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Server Agent jobs are crucial: if they are not running, system performance will degrade over time.  

- **Verify that the BizTalk Server SQL Server Agent jobs are completing in a timely manner**  

   Set up Microsoft System Center Operations Manager to monitor the jobs.  

   You should be aware of schedules that are particular to certain jobs:  

  -   The MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job runs continuously by default. Monitoring software should take this schedule into account and not produce warnings.  

  -   The MessageBox_Message_Cleanup_BizTalkMsgBoxDb job is not enabled or scheduled, but it is started by the MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job every 10 seconds. Therefore, this job should not be enabled, scheduled, or manually started.  

- **Verify that the Startup type of the SQL Server Agent service is configured correctly**  

   Verify that the SQL Server Agent service is configured with a **Startuptype** of **Automatic** unless the SQL Server Agent service is configured as a cluster resource on a Windows Server cluster. If the SQL Server Agent service is configured as a cluster resource, then you should configure the **Startuptype** as **Manual** since the service will be managed by the Cluster service.  

## Additional Resources  

- For more information about monitoring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Agent jobs, see [Monitoring SQL Server Agent Jobs and Databases](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md).  

- For more information about the SQL Server Agent jobs that are included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] see ["Database Structure and Jobs"](http://go.microsoft.com/fwlink/?LinkID=153451) (<http://go.microsoft.com/fwlink/?LinkID=153451>).
