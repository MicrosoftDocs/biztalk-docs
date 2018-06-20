---
title: "How to Modify .NET CLR Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Bts10.settings.HostInstanceCLR"
ms.assetid: 085743d8-27a6-4d8b-98c7-bb5b5c75848c
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Modify .NET CLR Settings
To update the number of Windows threads available in the .NET thread pool associated with an instance of a BizTalk host, you can modify the appropriate Common Runtime Language (CLR) Hosting values using the BizTalk Settings Dashboard. This topic provides the step-by-step procedure to modify these settings.  

## Prerequisites  
 To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.  

### To modify the .NET CLR settings of a host instance  

1. In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.  

2. In the **BizTalk Settings Dashboard** dialog box, on the **Host Instance** tab, click the **.NET CLR** tab.  

3. Do the following and click **Apply** to apply the modifications and proceed to another tab. Or click **OK** to apply the modifications and exit the Settings Dashboard.  


   |     Use this      |                                                                                To do this                                                                                | Boundary values | Default value | Upgrade logic |
   |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|---------------|---------------|
   | **Host Instance** | From the drop-down box, select the running instance of a host on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime machine. |        -        |       -       |       -       |

    **Threading Settings**  

   |Use this|To do this|Boundary values|Default value|Upgrade logic|  
   |--------------|----------------|---------------------|-------------------|-------------------|  
   |**Max. worker threads**|Specify the maximum number of .NET CLR worker threads.|[Min worker threads, 500]|25|Migrate the host instance registry settings to host instance settings, ignore Version, Flavor, Flags, and MinCompletionPortThreads.|  
   |**Min. worker threads**|Specify the minimum number of .NET CLR worker threads.|[0, 500]|5|Migrate the host instance registry settings to host instance settings, ignore Version, Flavor, Flags, and MinCompletionPortThreads.|  
   |**Max. IO threads**|Specify the maximum number of IO threads.|[Min IO threads, 1000]|250|Migrate the host instance registry settings to host instance settings, ignore Version, Flavor, Flags, and MinCompletionPortThreads.|  
   |**Min. IO threads**|Specify the minimum number of IO threads.|[0, 1000]|25|Migrate the host instance registry settings to host instance settings, ignore Version, Flavor, Flags, and MinCompletionPortThreads.|  

    .NET CLR Settings are per-core CPU.  

   > [!NOTE]
   >  To restore the default settings, click **Restore Defaults**.  

   > [!NOTE]
   >  **Worker threads** are used to handle queued work items and **I/O threads** are dedicated callback threads associated with an I/O completion port to handle a completed asynchronous I/O request.  

   > [!NOTE]
   >  If BizTalk is upgraded from a previous version, the values in the HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc$*hostname*\CLR Hosting registry key will be set in Settings Dashboard.  

## See Also  
 [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md)