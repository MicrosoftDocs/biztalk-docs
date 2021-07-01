---
description: "Learn more about: Troubleshooting BizTalk Server Tools"
title: "Troubleshooting BizTalk Server Tools | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 038a5f5c-d6eb-42db-88d6-70f3deba7a8a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting BizTalk Server Tools
This topic provides a centralized location for information about common problems encountered while using the tools included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].

## Known Issues

### BizTalk Server Tools and Utilities May Not Function Correctly on a Windows System That Supports UAC
 **Problem**

 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a system that supports User Account Control (UAC), the tools included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may not launch successfully, or may not function correctly.

 **Cause**

 When running an application that has been flagged for a specific privilege level, if the required level is higher than that of the user running the application, the UAC will display a prompt that allows you to temporarily elevate the application privilege to the required level. The tools shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not have the correct flags enabled to automatically request privilege elevation, so the tool will attempt to run at the current privilege level of the user running the application and will fail if a higher privilege level is required.

 **Resolution**

 To resolve this problem, run all BizTalk Server tools with Administrative privileges. To run a tool with Administrative privileges, right-click the application and then select **Run as administrator**.

 For more information about the User Account Control, see [https://go.microsoft.com/fwlink/?LinkId=99167](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc709691(v=ws.10)).

### Sometimes BizTalk Mapper Toolbox May Appear Empty
 **Problem**

 Sometimes, when you open the Mapper toolbox in Visual Studio, you do not see any functoids in the toolbox.

 **Cause**

 Might be a probable corruption by install/uninstall of Visual Studio add-ins and/or patch(es).

 **Resolution**

 To resolve this problem:

1.  Close all running instances of Visual Studio.

2.  Start **Visual Studio Command Prompt** as an administrator.

3.  At the command prompt, type the following command:

    ```
    devenv.exe /setup
    ```