---
title: "Update Group Settings | Microsoft Docs"
description: Change the performance settings of the group using BizTalk Server Administration
ms.custom: ""
ms.date: "06/08/2017"
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
Using the Settings Dashboard, you can modify the configuration information used across all machines in a given BizTalk group. This topic provides the step-by-step procedure to modify the group-level performance settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. These settings are applicable for all the machines in a given group.  

> [!NOTE]
>  You can also modify the host and host instance settings. For more information, see [How to Modify Host Settings](../core/how-to-modify-host-settings.md) and [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md).  

 The current BizTalk Server settings can be exported to an XML file. Later, you can import those settings to the Settings Dashboard instead of setting up new values. For information on importing or exporting the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) and [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md). 

## Prerequisites  
 To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.  

## Update the group-level settings  

1. In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.  

2. In the **BizTalk Settings Dashboard** dialog box, on the **Group** page, do the following:  


   |                       Use this                        |                                                                                                                                                                                          To do this                                                                                                                                                                                           |          Boundary values          | Default value |                                                Upgrade logic                                                |
   |-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|---------------|-------------------------------------------------------------------------------------------------------------|
   |          **Configuration refresh interval**           |                                                                                                                        Set the interval in which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] refreshes messaging configuration.                                                                                                                        |             1 - 43200             |       -       |                                                      -                                                      |
   |              **Message Batch Threshold**              |                                                                                                                                    If the total size of an incoming message Batch exceeds this value, then it is split into smaller batches and processed.                                                                                                                                    |           1 - 10000000            |    102400     | Copies the HKEY_LOCAL_MACHINE\Software\Microsoft\BizTalk Server\3.0\Administration\TransformThreshold value |
   |                **Large message size**                 |                                                                                                                                       Set the threshold size of an individual message that triggers streaming in a batch and/or during transformations.                                                                                                                                       |           1 - 10000000            |    1000000    |           Maximum of the existing **Large message size** and **LargeMessageFragmentSize** values.           |
   |              **Tracking and Reporting**               |                                                                                                                                                                                                                                                                                                                                                                                               |                 -                 |       -       |                                                      -                                                      |
   | **Message box performance counter sampling interval** |                                                                       Set the interval at which performance counters are refreshed.<br /><br /> The interval trades off load on database versus up-to-dateness of counters. The higher value means less frequently updated data, and thus lesser load on the database.                                                                        | 1 – Maximum value of type Integer |       -       |               Largest value on any machine in the BizTalk group if present. If not, default.                |
   |            **Enable group level tracking**            | Select this option to turn the group level tracking for BizTalk Server on.<br /><br /> Turning off global tracking disables the tracking interceptors for the entire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. This means, BizTalk Server will not track events in its tracking tables. **Note:**  This setting does not impact BAM Tracking. |              On, Off              |      On       |                                                      -                                                      |


3. Click **Apply** to apply the modifications and proceed to another tab. Or click **OK** to apply the modifications and exit the Settings Dashboard.  

   > [!NOTE]
   >  To restore the default settings, click **Restore Defaults**.  

## See Also  
 [Use Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)