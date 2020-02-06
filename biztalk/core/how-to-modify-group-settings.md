---
title: "Update Group Settings | Microsoft Docs"
description: Change the performance settings of the group using BizTalk Server Administration
ms.custom: "biztalk-2020"
ms.date: "01/22/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe0cbeb8-23d6-45cf-8535-c989914f5124
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to update the BizTalk group settings
Using the Settings Dashboard, you can modify the configuration information used across all machines in a given BizTalk group. This topic provides the step-by-step procedure to modify the group-level performance settings in BizTalk Server. These settings are applicable for all the machines in a given group.  

> [!NOTE]
>  You can also modify the host and host instance settings. For more information, see [How to Modify Host Settings](../core/how-to-modify-host-settings.md) and [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md).  

 The current BizTalk Server settings can be exported to an XML file. Later, you can import those settings to the Settings Dashboard instead of setting up new values. For information on importing or exporting the BizTalk Server settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) and [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md). 

## Prerequisites  
 To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.  

## Update the group-level settings  

1. In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.  

2. In the **BizTalk Settings Dashboard** dialog box, on the **Group** page, do the following:  


   |                       Use this                        |                                                                                                                                                                                          To do this                                                                                                                                                                                           |          Boundary values          | Default value |                                                Upgrade logic                                                |
   |-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|---------------|-------------------------------------------------------------------------------------------------------------|
   |          **Configuration refresh interval**           |                                                                                                                        Set the interval in which BizTalk Server refreshes messaging configuration.                                                                                                                        |             1 - 43200             |       -       |                                                      -                                                      |
   |              **Message Batch Threshold**              |                                                                                                                                    If the total size of an incoming message Batch exceeds this value, then it is split into smaller batches and processed.                                                                                                                                    |           1 - 10000000            |    102400     | Copies the HKEY_LOCAL_MACHINE\Software\Microsoft\BizTalk Server\3.0\Administration\TransformThreshold value |
   |                **Large message size**                 |                                                                                                                                       Set the threshold size of an individual message that triggers streaming in a batch and/or during transformations.                                                                                                                                       |           1 - 10000000            |    1000000    |           Maximum of the existing **Large message size** and **LargeMessageFragmentSize** values.           |
   |              **Receive Location**                     |
   |              **Enable fault tolerance**               | Select this option to allow receive locations to recover from transient errors instead of getting completely disabled. On error, receive locations will be disabled in the host instance where it is faulted and BizTalk will attempt to recover it in certain configurable interval. The receive location will continue running in other host instances.<br /><br />This setting applies to: <ul><li>BizTalk Server 2020 and newer</li></ul> |              On, Off              |      Off       |
   |              **Retry interval**                       | Set the interval in which BizTalk server attempts to recover receive location from failures.<br /><br />This setting applies to: <ul><li>BizTalk Server 2020 and newer</li></ul>                                                                        | 1 – 43200 |       60       |              -               |                                                  -                                                      |
   |              **Tracking and Reporting**               |                                                                                                                                                                                                                                                                                                                                                                                               |                 -                 |       -       |                                                      -                                                      |
   | **Message box performance counter sampling interval** |                                                                       Set the interval at which performance counters are refreshed.<br /><br /> The interval trades off load on database versus up-to-dateness of counters. The higher value means less frequently updated data, and thus lesser load on the database.                                                                        | 1 – Maximum value of type Integer |       -       |               Largest value on any machine in the BizTalk group if present. If not, default.                |
   |            **Enable group level tracking**            | Select this option to turn the group level tracking for BizTalk Server on.<br /><br /> Turning off global tracking disables the tracking interceptors for the entire BizTalk Server group. This means, BizTalk Server will not track events in its tracking tables. **Note:**  This setting does not impact BAM Tracking. |              On, Off              |      On       |                                                      -                                                      |
   |            **Allow import of tracking settings**      | Select this option allow import of tracking settings while a binding file is imported. When unchecked, import of binding file will not impact BizTalk application artifact tracking settings.<br /><br />This setting applies to: <ul><li>BizTalk Server 2016 and newer</li></ul> |              On, Off              |      On       |
   |            **Audit management Operations**            | Select this option to enable audit of management operations.<br /><br />This setting applies to: <ul><li>BizTalk Server 2020 and newer</li></ul> |              On, Off              |      Off       |
   |            **Maximum number of audit entries**        | Set the maximum number of audit logs to be retained in  audit store. BizTalk will automatically delete oldest records when number of audit entries exceeds this number.<br /><br />This setting applies to: <ul><li>BizTalk Server 2020 and newer</li></ul> | 1 – Maximum value of type Integer |       10000       |              -               |
   |             **Analytics**                             |
   |            **Enable group-level analytics**           | Select this option to leverage the power of Azure (Application Insights and Azure Event Hubs) to monitor your BizTalk applications.<br /><br />This setting applies to: <ul><li>BizTalk Server 2020 and newer</li> <li>BizTalk Server 2016 with Feature Pack 1 and newer</li></ul>  |              On, Off              |      Off       |
   |            **Target type**                            | Select the service in Azure(**Application Insights** or **Azure Event Hubs**) to which you wish to send analytics data.<br /><br />This setting applies to: <ul><li>BizTalk Server 2020 and newer</li> <li>BizTalk Server 2016 with Feature Pack 1 and newer</li></ul> |              -              |      None selected       |
   |            **Connection parameters**                  | Set connection parameters of the Azure service where monitoring data will be analyzed. <br /><br /> You can either manually enter the connection parameters or sign-in to azure and get connection details.<br /><br />This setting applies to: <ul><li>BizTalk Server 2020 and newer</li> <li>BizTalk Server 2016 with Feature Pack 1 and newer</li></ul>  |              -              |     Empty      |

3. Click **Apply** to apply the modifications and proceed to another tab. Or click **OK** to apply the modifications and exit the Settings Dashboard.  

   > [!NOTE]
   >  To restore the default settings, click **Restore Defaults**.  

## See Also  
 [Use Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)
