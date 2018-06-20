---
title: "How to View Instance Information for a Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send ports, viewing"
  - "managing [send ports], viewing"
  - "viewing, send ports"
ms.assetid: 37cf6561-5341-4a05-b531-33ab0334966e
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to View Instance Information for a Send Port
This topic describes how to use the BizTalk Server Administration console to view a list of the running service instances of a send port. A service instance is an instance of the send port service that is created when a message is sent to the send port. When you follow the procedure in this topic, instance information displays in the Group Overview page for the send port.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To view instance information for a send port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to view service instance information for a send port.  
  
3. Click **Send Ports**, right-click the send port, point to **View**, and then click **Instance Information**.  
  
    The query results panel in the lower section of the page displays all running instances of the send port.  
  
4. To refine the query and view different service instance information for the send port, click the box under **Value** for the Search For field, select the instance type to view, and then click **Run Query**. For more information about creating queries, see the topics on searching under See Also.  
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)   
 [How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md)   
 [How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md)   
 [How to Search for Messages](../core/how-to-search-for-messages.md)   
 [How to Search for Subscriptions](../core/how-to-search-for-subscriptions.md)