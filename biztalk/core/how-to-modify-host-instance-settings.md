---
title: "Update Host Instance Settings | Microsoft Docs"
description: Change the host instance settings in BizTalk Server Administrator
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2338255b-cc13-4f6a-86c3-9ecc666c43e5
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update BizTalk host instance settings

## Overview
Using the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)], you can modify the configuration information of a given host instance, across a BizTalk group. This topic provides the step-by-step procedure to modify the host instance level performance settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Often you have the BizTalk settings (from a source environment) saved as an XML file. The XML file contains information that allows you to replicate the settings on the target machine. You can import those settings to Settings Dashboard, instead of setting up new values. On the other hand, after setting up new values for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can export them to an XML file to be used in another machine.  
  
 For information on importing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) and [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md). 
  
## Prerequisites  
 To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.  
  
## Update the host instance level settings  
  
1. In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.  
  
2. In the **BizTalk Settings Dashboard** dialog box, on the **Host Instances** tab, do any of the following:  
  
   -   Modify the .NET CLR settings for a host instance. See [Change the .NET CLR Settings](../core/how-to-modify-net-clr-settings.md).  
  
   -   Modify the orchestration memory throttling settings. See [Change the Orchestration Memory Throttling Settings](../core/how-to-modify-orchestration-memory-throttling-settings.md).  
  
## See Also  
 [Use Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)