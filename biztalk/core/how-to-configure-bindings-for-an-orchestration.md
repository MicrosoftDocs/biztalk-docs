---
title: "Configure Bindings for an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9724a3a0-c217-4f98-b6d9-21f788ce50ba
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Bindings for an Orchestration

## Overview
This topic describes how to use the BizTalk Server Administration console to configure bindings for an orchestration. This involves binding the logical ports defined for the orchestration to physical ports in the staging or production environment as well as binding the orchestration to a host. If the orchestration has already been bound, you can change the bindings by using this procedure.  
  
 After configuring bindings, you can enlist the orchestration and then start it so that it begins processing messages. For instructions on performing these tasks, see [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) and [How to Start an Orchestration](../core/how-to-start-an-orchestration.md).  
  
> [!NOTE]
>  The application developer can configure bindings for an orchestration to test its functionality during the development process either by using the procedure in this topic. You can also use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## Configure bindings for an orchestration  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration for which you want to configure bindings  
  
3. Click **Orchestrations**, right-click the orchestration for which you want to configure bindings, and then click **Properties**.  
  
4. Click the **Bindings** tab, and from the **Host** list, select the host on which to enlist an orchestration.  
  
5. From the drop-down lists in the **Receive Ports** column, next to each inbound logical port, select the receive port to which you want to bind the logical port.  
  
6. From the drop-down list in the **Send Ports/Send Port Groups** column, next to each inbound logical port, select the send port to which you want to bind the logical port, and then click **OK**.  
  
## See Also  
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md)   
 [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md)