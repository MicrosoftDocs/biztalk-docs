---
title: "How to Edit the Console Colors for BTSTask | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 725dcb7b-5a19-4166-9d1c-93f30ddca201
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Edit the Console Colors for BTSTask
This topic describes how to edit the foreground colors that BTSTask outputs to the console. If your console background color is white, you will have difficulty reading the default BTSTask console output and will need to modify the console foreground colors.  
  
## Prerequisites  
 To perform the procedure in this topic, you must have Read/Write permissions on the BTSTask.exe.config file contained in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder.  
  
### To edit the console foreground colors for BTSTask  
  
1. On the computer where you want to run BTSTask, open BTSTask.exe.config in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] or a text or XML editor. This file is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder.  
  
2. Edit the values for the Console.ForegroundColor.Error, Console.ForegroundColor.Warning, and Console.ForegroundColor.Info keys according to the console foreground colors that you want for error messages, warnings, and information, respectively, and then save the file. (For monochrome, delete these three entries, rather than editing their values.)  
  
    The available values for foreground colors are as follows:  
  
    0: Black  
  
    1: DarkBlue  
  
    2: DarkGreen  
  
    3: DarkCyan  
  
    4: DarkRed  
  
    5: DarkMagenta  
  
    6: DarkYellow  
  
    7: Gray  
  
    8: DarkGray  
  
    9: Blue  
  
    10: Green  
  
    11: Cyan  
  
    12: Red  
  
    13: Magenta  
  
    14: Yellow  
  
    15: White  
  
## See Also  
 [BTSTask Command-Line Reference](../core/btstask-command-line-reference.md)