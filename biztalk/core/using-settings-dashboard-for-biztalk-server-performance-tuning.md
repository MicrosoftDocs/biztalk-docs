---
title: "Using Settings Dashboard for BizTalk Server Performance Tuning | Microsoft Docs"
description: Use Settings Dashboard in BizTalk Server Adminstration to update group, host, and host instance settings 
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bb1ddac-1e8f-4928-9c70-8326ae64a734
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Use Settings Dashboard for BizTalk Server Performance Tuning

## Overview
Using the Settings Dashboard, you can extensively tweak [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings for performance optimization. You can also modify settings for the BizTalk Group, BizTalk Host, and BizTalk Host Instance.  
  
- **Group-level settings**: At the group level, you can use the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] to set properties like the configuration refresh interval, maximum message batch size, group level tracking, etc. These settings are applied to all machines in a BizTalk Group.  
  
- **Host-level settings**: At the host level, you can modify settings like host tracking, properties related to resource based throttling, properties related to message process throttling, and properties related to orchestrations throttling. These settings are applied to all instances of the selected host.  
  
- **Host instance level settings**: At the host instance level, you can modify .NET CLR settings and properties related to orchestration memory throttling. These settings are applied to only the selected host instance.  
  
  For more information about BizTalk Group, BizTalk Host, and BizTalk Host Instance settings, see [How to Modify Group Settings](../core/how-to-modify-group-settings.md), [How to Modify Host Settings](../core/how-to-modify-host-settings.md), and [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md).  
  
  The Settings Dashboard enables you to import/export BizTalk settings across deployments that need not be identical. Using the user interface, you can map the hosts and host instances from destination to source deployments. This helps you apply settings to an environment where host and machine names, or their respective counts, are different. For more details about importing/exporting BizTalk settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md).  
  
## See Also  
 [Manage BizTalk Server Performance Settings](../core/managing-biztalk-server-performance-settings.md)