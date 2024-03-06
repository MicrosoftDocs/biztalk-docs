---
title: BizTalk Settings Dashboard, Group Page
description: Read about the settings on the dashboard, including receive locations, tracking, and more.
ms.service: biztalk-server
ms.topic: conceptual
ms.date: 02/10/2020
---

# BizTalk Settings Dashboard, Group Page

Use the **Group** tab to modify the configuration of group-level performance settings in BizTalk Server.

## Apply to all computers in the group

- **Configuration refresh interval**: Set the interval in which BizTalk Server refreshes messaging configuration, from 1 - 43200.
- **Message Batch Threshold**: If the total size of an incoming message batch exceeds this value, then it's split into smaller batches and processed. Enter a value between 1 - 10000000. Default value is `102400`.
- **Large message size**: Set the threshold size of an individual message that triggers streaming in a batch and/or during transformations. Enter a value between 1 - 10000000. Default value is `1000000`.

## Receive locations

These settings apply to: BizTalk Server 2020 and newer

- **Enable fault tolerance**: When set to **On**, receive locations recover from transient errors, and aren't disabled. When set to **Off** (default), receive locations with transient errors are disabled in the faulty host instance, and BizTalk tries to recover the receive locations using the **Retry interval** value you enter. The receive location continues to run in other host instances.
- **Retry interval**: Set the interval, from 1 – 43200, for BizTalk server to recover receive locations from failures. Default value is `60`.

## Tracking and reporting

- **Message box performance counter sampling interval**: Enter the interval to refresh the performance counters, from 1 – Maximum value of type Integer. The interval trades off load on database versus up-to-dateness of counters. The higher value means less frequently updated data, and lesser load on the database.
- **Enable group level tracking**: Select **On** to turn the group level tracking for BizTalk Server on. Turning off global tracking disables the tracking interceptors for the entire BizTalk Server group. So, BizTalk Server will not track events in its tracking tables. This setting doesn't impact BAM Tracking. Default is **On**.
- **Allow import of tracking settings**: Select **On** (default) to allow import of tracking settings when a binding file is imported. In versions older than BizTalk Server 2016, tracking settings are imported with the binding file. When unchecked, the tracking settings aren't imported. This is a global setting, so it applies to all applications you import, and will import in the future.

  If you want to control what is specifically tracked in your environments, just as you have in previous BizTalk versions, then leave this setting enabled. If you want to disable tracking on all artifacts on all imported applications, then uncheck this setting.

  BTS task example: `btstask importbindings -ImportTrackingSettings:false -Source:c:\temp\binding.xml`

  This setting applies to:

  - BizTalk Server 2016 and newer

- **Audit management operations**: Select **On** to enable audit of management operations. Default is **Off**.

  This setting applies to:

  - BizTalk Server 2020 and newer

- **Maximum number of audit entries**: Enter the maximum number of audit logs to keep in the audit store, from 1 – Maximum value of type Integer. BizTalk will automatically delete oldest records when number of audit entries exceeds this number. Default is `10000`.

  This setting applies to:

  - BizTalk Server 2020 and newer

## Analytics

These settings apply to: BizTalk Server 2016 Feature Pack 1 and newer

- **Enable group-level analytics**: Select **On** to use Azure Application Insights and Azure Event Hubs to monitor your BizTalk applications. Default is **Off**.

  Turning off global analytics disables the analytics interceptors for the entire BizTalk Server group. When **Off**, BizTalk Server doesn't collect analytics events.

- **Target type**: Select Azure **Application Insights** or **Azure Event Hubs** to send analytics data.
- **Connection parameters**: Enter connection parameters of the Azure service where monitoring data is analyzed. You can manually enter the connection parameters, or sign-in to Azure and get connection details.

## Restore, import, and export

- **Restore defaults**: Cancels your changes, and applies the default BizTalk Server settings.
- **Import**: Import the group, host, and host instance settings that have been exported from another group.
- **Export**: Export the group, host, and host instance settings from this current BizTalk group, to an XML file.

## See Also

[How to Modify Host Settings](/biztalk/core/how-to-modify-host-settings)  
[How to Modify Host Instance Settings](/biztalk/core/how-to-modify-host-instance-settings)