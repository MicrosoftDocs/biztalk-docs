---
title: "Update Group Settings | Microsoft Docs"
description: Change the performance settings of the group using BizTalk Server Administration
ms.custom: "biztalk-2020"
ms.date: "02/10/2020"
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

# Update the BizTalk group settings

Using the Settings Dashboard, you can modify the configuration information used across all machines in a given BizTalk group. This topic provides the step-by-step procedure to modify the group-level performance settings in BizTalk Server. These settings are applicable for all the machines in a given group.  

> [!NOTE]
>  You can also modify the host and host instance settings. For more information, see [How to Modify Host Settings](../core/how-to-modify-host-settings.md) and [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md).  

 The current BizTalk Server settings can be exported to an XML file. Later, you can import those settings to the Settings Dashboard instead of setting up new values. For information on importing or exporting the BizTalk Server settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) and [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md). 

## Prerequisites

Sign in as a member of the BizTalk Server Administrators group.  

## Update the group-level settings  

1. In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.  

2. In the **BizTalk Settings Dashboard** dialog box, on the **Group** page, do the following:

    - **Configuration refresh interval**: Set the interval for BizTalk Server to refresh the messaging configuration, from 1 - 43200.
    - **Message Batch Threshold**: If the total size of an incoming message batch exceeds this value, then it is split into smaller batches and processed. Enter a value between 1 - 10000000. Default value is `102400`.

      In an upgrade, the `HKEY_LOCAL_MACHINE\Software\Microsoft\BizTalk Server\3.0\Administration\TransformThreshold` value is copied.

    - **Large message size**: Set the threshold size of an individual message that triggers streaming in a batch and/or during transformations. Enter a value between 1 - 10000000. Default value is `1000000`. 

      In an upgrade, this value is set to the maximum of the existing **Large message size** and **LargeMessageFragmentSize** values.

    - **Enable fault tolerance**: When set to **On**, receive locations recover from transient errors, and aren't disabled. When set to **Off** (default), receive locations with transient errors are disabled in the faulty host instance, and BizTalk tries to recover the receive locations using the **Retry interval** value you enter. The receive location continues to run in other host instances.
    
    This setting applies to:  
      - BizTalk Server 2020 and newer

    - **Retry interval**: Set the interval, from 1 – 43200, for BizTalk server to recover receive locations from failures. Default value is `60`.

    This setting applies to:  
      - BizTalk Server 2020 and newer

    - **Message box performance counter sampling interval**: Enter the interval to refresh the performance counters, from 1 – Maximum value of type Integer. The interval trades off load on database versus up-to-dateness of counters. The higher value means less frequently updated data, and lesser load on the database.

      In an upgrade, if there's an existing value, then the largest value on any server in the BizTalk group is used. If not, the default is used.

    - **Enable group level tracking**: Select **On** to turn the group level tracking for BizTalk Server on. Turning off global tracking disables the tracking interceptors for the entire BizTalk Server group. So, BizTalk Server will not track events in its tracking tables. This setting doesn't impact BAM Tracking. Default is **On**.
    - **Allow import of tracking settings**: Select **On** to allow import of tracking settings when a binding file is imported. When unchecked, import of binding file will not impact BizTalk application artifact tracking settings. Default is **On**.

    This setting applies to:  
      - BizTalk Server 2016 and newer

    - **Audit management operations**: Select **On** to enable audit of management operations. Default is **Off**.
    
      This setting applies to:  
        - BizTalk Server 2020 and newer

    - **Maximum number of audit entries**: Enter the maximum number of audit logs to keep in the audit store, from 1 – Maximum value of type Integer. BizTalk will automatically delete oldest records when number of audit entries exceeds this number. Default is `10000`.

      This setting applies to:  
        - BizTalk Server 2020 and newer

    - **Enable group-level analytics**: Select **On** to use Azure Application Insights and Azure Event Hubs to monitor your BizTalk applications. Default is **Off**.

      This setting applies to:  
        - BizTalk Server 2020 and newer
        - BizTalk Server 2016 Feature Pack 1 and newer

    - **Target type**: Select Azure **Application Insights** or **Azure Event Hubs** to send analytics data.

      This setting applies to:  
        - BizTalk Server 2020 and newer
        - BizTalk Server 2016 Feature Pack 1 and newer

    - **Connection parameters**: Enter connection parameters of the Azure service where monitoring data is analyzed. You can manually enter the connection parameters, or sign-in to Azure and get connection details.

      This setting applies to:  
        - BizTalk Server 2020 and newer
        - BizTalk Server 2016 Feature Pack 1 and newer

3. Click **Apply** to apply the modifications and proceed to another tab. Or click **OK** to apply the modifications and exit the Settings Dashboard.  

    To restore the default settings, select **Restore Defaults**.  

## See Also

[Use Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)
