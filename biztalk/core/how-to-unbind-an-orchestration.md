---
title: "Unbind an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a7c421d-e0cb-4b23-b472-e501056d6329
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Unbind an Orchestration

## Overview
This topic describes how to use the BizTalk Server Administration console to remove receive port, send port, or host bindings from an orchestration.  
  
> [!NOTE]
>  The application developer can remove bindings for an orchestration  by using the procedure in this topic. You can also use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## Remove bindings from an orchestration  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration from which you want to remove bindings  
  
3. Click **Orchestrations**, right-click the orchestration, click **Properties**, and then click **Bindings** in the left pane.  
  
4. To remove the host bindings, from the **Hosts** list, select **\<None\>**.  
  
5. To remove receive port bindings, from the drop-down list under **Receive Ports**, click **\<None\>**.  
  
6. To remove send port bindings, from the drop-down list under **Send Ports/Send Port Groups**, click **\<None\>**.  
  
7. When finished removing bindings, click **OK**.  
  
## See Also  
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md)   
 [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md)