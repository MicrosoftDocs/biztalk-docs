---
title: "How to Export BizTalk Settings Using BTSTask | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27b3ee9c-2bed-416a-8724-d68d1008d85f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export BizTalk Settings Using BTSTask
BizTalk Server administrators try to tune BizTalk Server performance in a test environment to achieve the desired performance results. Upon achieving satisfactory results, the administrators can use the BTSTask command-line utility to export the BizTalk erver settings of the source environment to an XML file. These settings can later be imported to a production environment. This topic provides step-by-step procedure to export the BizTalk Server settings using **BTSTask.exe**.  
  
> [!IMPORTANT]
>  For information about how the BizTalk Server settings in an XML file are applied to the target environment, see [How to Import BizTalk Settings Using Settings Dashboard](../core/how-to-import-biztalk-settings-using-settings-dashboard.md) or [How to Import BizTalk Settings Using BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md).  
  
 You can also export the current settings using the Settings Dashboard. For more information, see [How to Export BizTalk Settings Using Settings Dashboard](../core/how-to-export-biztalk-settings-using-settings-dashboard.md).  
  
## To export BizTalk settings  
 You can use the **ExportSettings** command to export the BizTalk Server settings of the source environment to an XML file. For details about how to use the **ExportSettings** command in BTSTask.exe utility, see [ExportSettings Command](../core/exportsettings-command.md).  
  
## See Also  
 [Automating BizTalk Server Performance Tuning](../core/automating-biztalk-server-performance-tuning.md)