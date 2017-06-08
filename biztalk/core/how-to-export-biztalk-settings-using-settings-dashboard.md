---
title: "How to Export BizTalk Settings Using Settings Dashboard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5604f883-d502-4a82-b37e-33e062373081
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export BizTalk Settings Using Settings Dashboard
BizTalk Server administrators try to tune BizTalk Server performance in a test environment to achieve the desired performance results. Upon achieving satisfactory results, the administrators can use the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)], to export the BizTalk Server settings of the source environment to an XML file. These settings can later be imported to a production environment. This topic provides step-by-step procedure to export the BizTalk Group, Host, and Host Instance settings.  
  
> [!WARNING]
>  You should not manually edit the exported XML file because when you import this XML file to a production environment, the import process might fail due to some data type mismatch or other such errors introduced by manual editing.  
  
> [!IMPORTANT]
>  For information about importing the XML file to another environment and applying the BizTalk settings, see [How to Import BizTalk Settings Using Settings Dashboard](../core/how-to-import-biztalk-settings-using-settings-dashboard.md) or [How to Import BizTalk Settings Using BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md).  
  
 You can also use the BTSTask command-line utility to export the Group, Host, and Host Instance settings. For more information, see [How to Export BizTalk Settings Using BTSTask](../core/how-to-export-biztalk-settings-using-btstask.md).  
  
## Prerequisites  
 To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.  
  
### To export the BizTalk group, host, and host instance settings  
  
1.  In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.  
  
2.  In the **BizTalk Settings Dashboard** dialog box, click **Export**. The **Save As** dialog box appears.  
  
3.  Browse to the location where you want to save the current BizTalk settings. Enter the filename, select the type as XML format, and then click **Save**.  
  
## See Also  
 [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)