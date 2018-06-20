---
title: "How to View Instance Information for an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, viewing"
  - "managing [orchestrations], viewing"
ms.assetid: 860ac2b2-c556-4e1f-8b7f-18ab8be52db4
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to View Instance Information for an Orchestration
This topic describes how to view instance information for an orchestration by using the BizTalk Server Administration console. A service instance is an instance of an orchestration that BizTalk Server is either processing or has serialized into the MessageBox for further processing or tracking.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To view instance information for an orchestration  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration for which you want to view instance information.  
  
3. Click **Orchestrations**, select the orchestration for which you want to view instance information, click **View**, and then select **Instance Information**.  
  
    The query results panel in the lower section of the page displays all instances of the orchestration.  
  
    To refine the query and view different instance information for the orchestration, click the box under **Value** for the Search For field, select the instance type to view, and then click **Run Query**. For more information about creating queries, see the topics on searching under See Also.  
  
## See Also  
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md)   
 [How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md)   
 [How to Search for Messages](../core/how-to-search-for-messages.md)   
 [How to Search for Subscriptions](../core/how-to-search-for-subscriptions.md)