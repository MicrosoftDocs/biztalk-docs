---
title: "How to Display Monitors for a Management Pack | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7c4d2b3-9c01-40f5-b983-bf29a3a5cacc
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Display Monitors for a Management Pack
To display a list of outputs for a management pack's monitors and overrides using the Command Shell, use the following procedure.  
  
### To display monitors for a management pack  
  
1. In your management server, click **Programs**, and then click **System Center.**  
  
2. Click **Command Shell**.  
  
3. In the Command Shell, type the following command:   
   `get-scommanagementpack –DisplayName “DisplayName” | get-scommonitor | export.csv filename`  
  
4. A .csv file is created. The .csv file can be opened in Microsoft Office Excel.  
  
   > [!NOTE]  
   >  In Excel, you may be required to specify that the .csv file is a text file.  
  
   For example, the following command retrieves data for the monitors associated with one of the core management packs:   
   `get-scommanagementpack -DisplayName "BizTalk Server Monitoring" | Get-ScomMonitor | export-csv "c:\monitors.csv"`