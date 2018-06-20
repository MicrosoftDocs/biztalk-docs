---
title: "How to Unenlist an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, unenlisting"
  - "enlisting, unenlisting"
  - "managing [orchestrations], unenlisting"
  - "unenlisting, orchestrations"
ms.assetid: 038ed7bb-615c-4e4e-a5bb-79de2626de77
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Unenlist an Orchestration
This topic describes how to unenlist an orchestration by using the BizTalk Server Administration console. Unenlisting an orchestration removes it from the host. This removes the subscription so that the orchestration no longer processes messages. You must unenlist an orchestration before you can edit its bindings.  
  
 Before you can unenlist an orchestration, you must terminate any running instances, as described in [How to Suspend, Resume, and Terminate Orchestration Instances](../core/how-to-suspend-resume-and-terminate-orchestration-instances.md).  
  
> [!NOTE]
>  The application developer can unenlist an orchestration during the development process by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To unenlist an orchestration  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to unenlist.  
  
3. Click **Orchestrations**, right-click the orchestration to unenlist, and then click **Unenlist**.  
  
   > [!NOTE]
   >  To unenlist multiple orchestrations at once, hold down the shift key and select each orchestration to unenlist, right-click an orchestration, and then click **Unenlist**.  
  
## See Also  
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md)   
 [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md)