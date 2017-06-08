---
title: "How to Modify Host Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0759b3a0-560e-4a11-92e6-9de0e15f463b
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Modify Host Settings
Using the Settings Dashboard, you can modify the configuration information of a given host, across a BizTalk group. This topic provides the step-by-step procedure to modify the host-level performance settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  You can also modify the group and host instance settings. For information about how to modify the settings, see [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).  
  
 The current BizTalk Server settings can be exported to an XML file. Later, you can import those settings to the Settings Dashboard instead of setting up new values. For information about how to import the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings, see [How to Import BizTalk Settings Using Settings Dashboard](../core/how-to-import-biztalk-settings-using-settings-dashboard.md) and [How to Import BizTalk Settings Using BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md). For information about how to export the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings, see [How to Export BizTalk Settings Using Settings Dashboard](../core/how-to-export-biztalk-settings-using-settings-dashboard.md) and [How to Export BizTalk Settings Using BTSTask](../core/how-to-export-biztalk-settings-using-btstask.md).  
  
## Prerequisites  
 To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.  
  
### To modify the host-level settings  
  
1.  In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.  
  
2.  In the **BizTalk Settings Dashboard** dialog box, on the **Hosts** page, do one or more of the following.  
  
    -   Modify the general performance settings of the BizTalk host. For more information, see [How to Modify General Settings](../core/how-to-modify-general-settings.md).  
  
    -   Modify the resource-based throttling settings of the BizTalk host. For more information, see [How to Modify Resource Based Throttling Settings](../core/how-to-modify-resource-based-throttling-settings.md).  
  
    -   Modify the rate-based throttling settings of the BizTalk host. For more information, see [How to Modify Rate Based Throttling Settings](../core/how-to-modify-rate-based-throttling-settings.md).  
  
    -   Modify the orchestration throttling settings of the BizTalk host. For more information, see [How to Modify Orchestration Throttling Settings](../core/how-to-modify-orchestration-throttling-settings.md).  
  
## See Also  
 [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)