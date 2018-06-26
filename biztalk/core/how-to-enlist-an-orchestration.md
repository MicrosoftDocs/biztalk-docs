---
title: "How to Enlist an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [orchestrations], enlisting"
  - "orchestrations, enlisting"
  - "enlisting, orchestrations"
ms.assetid: b21a398b-8c9a-42ae-aac0-de35dbfd8176
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enlist an Orchestration
This topic describes how to use the BizTalk Server Administration console to enlist an orchestration into a host. The orchestration must be enlisted before you can start it.  
  
 When enlisting an orchestration, bear in mind the following points:  
  
-   **The orchestration must be bound before you can enlist it.** For instructions on configuring bindings for orchestrations, see [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).  
  
-   **Subscriptions are automatically created.** The orchestration enlistment process creates the necessary subscriptions in the MessageBox database.  
  
-   **You must install the application.** You must install the application containing the orchestration on all of computers where the orchestration will run. For more information, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).  
  
-   **A calling orchestration must be bound to the same host as the called orchestration.** Any orchestration that is called by another orchestration must be bound to the same host as the calling orchestration.  
  
-   **You should also enlist dependent orchestrations.** If you enlist an orchestration but do not enlist any dependent orchestrations, the dependent orchestrations will not have any subscriptions. A dependent orchestration without subscriptions may drop or suspend messages because there is no subscription for the messages to match.  
  
> [!NOTE]
>  The application developer can enlist an orchestration to test its functionality during the development process  by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To enlist an orchestration  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to enlist.  
  
3. Click **Orchestrations**, right-click the orchestration to enlist, and then click **Enlist**.  
  
   > [!NOTE]
   >  To enlist multiple orchestrations at once, hold down the shift key and select each orchestration to enlist, right-click an orchestration, and then click **Enlist**.  
  
    The orchestration is enlisted and the appropriate subscriptions are created. The orchestration is in the stopped state. To start processing incoming messages, you must explicitly start the orchestration by right-clicking it and clicking **Start**. For more information, see [How to Start an Orchestration](../core/how-to-start-an-orchestration.md).  
  
## See Also  
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [How to Unenlist an Orchestration](../core/how-to-unenlist-an-orchestration.md)