---
title: "Standalone MSBUILD | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21aa3693-3788-4874-b506-6f4584fb4fd5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Standalone MSBUILD
The **Project Build** component of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] allows you to build [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] solutions without [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To install the **Project Build** component on your server, select the **Project Build Component** option in the **Additional Software category** during installation. You should unselect the **Developer Tools and SDK** as you are installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a computer without [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 For more information on MSBUILD, see [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).  
  
## To build a BizTalk project  
  
1.  Click **Start**, and click **Run**.  
  
2.  Type **cmd**, and press ENTER.  
  
3.  Switch to the project directory, and run a MSBUILD command to build the BizTalk solution.  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!TIP]
    >  You may need set the PATH environment variable to point to the folder in which msbuild.exe resides (\<*windows installation directory*>\Microsoft.NET\Framework\v4).