---
description: "Learn more about: How to Display Overrides for a Management Pack"
title: "How to Display Overrides for a Management Pack"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Display Overrides for a Management Pack
To display overrides for a management pack, use the following procedure.  
  
### To display overrides for a management pack  
  
1. In your management server, click **Programs**, and then click **System Center**.  
  
2. Click **Command Shell**.  
  
3. In the Command Shell, type the following command:   
   `$mp = get-scommanagementpack -DisplayName "Operations Manager Internal Library"`   
   `$mp.GetOverrides()`  
  
4. A .csv file is created. The .csv file can be opened in Office Excel.  
  
   > [!NOTE]  
   >  In Office Excel, you may be required to specify that the .csv file is a text file.  
  
   For example, the following command displays the overrides for one of the core management packs:   
   `$mp = get-scommanagementpack -DisplayName "Contoso.BizTalk.Overrides.mp"`  
   `$mp.GetOverrides()`
