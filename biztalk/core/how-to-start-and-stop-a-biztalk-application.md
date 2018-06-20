---
title: "How to Start and Stop a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "starting"
  - "starting, applications"
  - "managing [applications], starting"
  - "managing [applications], stopping"
  - "applications, starting"
  - "stopping, applications"
  - "applications, stopping"
  - "stopping"
ms.assetid: f9f83e99-a1e2-4dfd-b3be-60d3ec2cbcc4
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Start and Stop a BizTalk Application
This topic describes how to use the BizTalk Server Administration console to start and stop a BizTalk application.  
  
 Before you can start an application, bindings must be configured for all orchestrations it contains, as described in [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).  
  
 When you start an application, you can select one or more of the following options, as follows:  
  
-   Enlist and start all orchestrations.  
  
-   Enlist and start all send ports.  
  
-   Enlist and start all send port groups.  
  
-   Enable all receive locations.  
  
-   Start all associated host instances.  
  
-   Resume suspended instances.  
  
-   Deploy all policies.  
  
> [!NOTE]
>  Only published policies in the application are deployed automatically. If a policy is not published, it will not be deployed.  
  
 When you stop an application, you can select one of the following options:  
  
-   **Partial Stop - Allow running instances to continue.** This option disables all receive locations in the application, but leaves all other artifacts in their previous state. This allows running instances to complete processing messages that are currently in the system. Note that if a message transaction requires multiple inputs, it may not be able to complete when you use this option.  
  
-   **Partial Stop - Suspend running instances.** This option disables all receive locations and stops all orchestrations and send ports in the application. It does not unenlist or undeploy any artifacts. Use this option when you want to temporarily pause the application.  
  
-   **Full Stop - Terminate instances.** This option disables all receive locations, stops and unenlists all orchestrations and send ports, and undeploys all policies in the application. Use this option when you want to completely undeploy an application. Note that any running instances that are still processing messages will not complete processing. For more information, see [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. BizTalk Operators can perform a partial stop, but not a full stop. In addition, BizTalk Operators can start an application if all artifacts are enlisted. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To start or stop a BizTalk application  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, and then expand **Applications**.  
  
3. Right-click the BizTalk application that you want to start or stop, and then click **Start** or **Stop**.  
  
4. Select the start or stop options you want and click **Start** or **Stop**.  
  
## See Also  
 [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md)   
 [Updating BizTalk Applications](../core/updating-biztalk-applications.md)