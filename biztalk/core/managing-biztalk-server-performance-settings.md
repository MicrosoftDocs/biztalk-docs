---
title: "Managing BizTalk Server Performance Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca56a981-a255-4c4d-82f8-a57d390e425e
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing BizTalk Server Performance Settings
In the previous releases of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], users had to access the settings at multiple places/through multiple processes, such as:  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console  
  
-   Tweaking registry keys  
  
-   Configuration files  
  
-   Modifying BizTalk Management database tables  
  
 The [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] in [!INCLUDE[prague](../includes/prague-md.md)] collates all these settings and provides a central console to manage them. This helps in:  
  
-   Improving the discoverability of the properties that can be set.  
  
-   Reducing the time-to-solution because all settings are now accessible in a single place and can be exported/imported easily.  
  
-   Offering a holistic view of level of performance tuning done on a given BizTalk deployment.  
  
## Settings Dashboard User Interface  
 The [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] is targeted towards IT administrators who need to extensively tweak [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings for performance optimization.  
  
 You can use the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] to modify settings for the BizTalk Group, and all the BizTalk Hosts and BizTalk Host Instances in that Group.  
  
 To know more about the group, host, and host instance settings, see [How to Modify Group Settings](../core/how-to-modify-group-settings.md), [How to Modify Host Settings](../core/how-to-modify-host-settings.md), and [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md).  
  
## Prerequisites to Launch the Settings Dashboard  
 You can launch the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. For information on how to manage [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance settings using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).  
  
## Where Do I Start?  
 You can access the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] in any of the following ways:  
  
-   Start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **BizTalk Group** in the console tree, and then select **Settings**.  
  
-   Right click any host under the **Platform Settings** node in MMC and click on **Settings**. This launches [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] and you can modify the settings related to that host.  
  
-   Right click any host instance under the **Platform Settings** node in MMC and click on **Settings**. This launches [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] and you can modify the settings related to that host instance.  
  
## Exporting and Importing the BizTalk Server Settings  
 The [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] can be used to export settings from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment and import it into another [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, thereby reducing the overall time-to-solution. This is especially useful in scenarios where the administrators try to tune [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance in a test environment, and upon achieving the desired results, they can import the settings into a production environment.  
  
 For information about how to import/export using the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] user interface, see [How to Import BizTalk Settings Using Settings Dashboard](../core/how-to-import-biztalk-settings-using-settings-dashboard.md) and [How to Export BizTalk Settings Using Settings Dashboard](../core/how-to-export-biztalk-settings-using-settings-dashboard.md).  
  
## Support for Scripting  
 The [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] not only provides a central user interface to manage BizTalk settings but also ensures that all settings and the import/export tasks are accessible via APIs and command-line options. This enables BizTalk Server administrators to automate tasks related to BizTalk Server settings. As part of the scripting support:  
  
-   All group settings can be accessed and modified via the WMI Class: `MSBTS_GroupSetting`  
  
-   All host settings can be accessed and modified via the WMI Class: `MSBTS_HostSetting`  
  
-   All host instance settings can be accessed and modified via the WMI Class: `MSBTS_HostInstanceSetting`  
  
-   Import and export operations can be accessed through **BTSTask.exe** commands: `ExportSettings` and `ImportSettings`  
  
 For details about how to import/export using the BTSTask.exe command-line utility, see [How to Import BizTalk Settings Using BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md) and [How to Export BizTalk Settings Using BTSTask](../core/how-to-export-biztalk-settings-using-btstask.md).  
  
## In this Section  
  
-   [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)  
  
-   [Automating BizTalk Server Performance Tuning](../core/automating-biztalk-server-performance-tuning.md)  
  
## See Also  
 [Managing BizTalk Server](../core/use-groups-create-artifacts-optimize-performance-and-more-in-biztalk-server.md)