---
title: "How to View Instance Information for a Receive Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [receive ports], viewing"
  - "receive ports, viewing"
  - "viewing, receive ports"
ms.assetid: dad038bc-1202-489b-b144-a93bf1f53c0c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to View Instance Information for a Receive Port
This topic describes how to use the BizTalk Server Administration console to view the service instances for a receive port. Each time the receive port receives a message, a service instance is created to process the message. When you follow the procedure in this topic, instance information displays in the Group Overview page for the receive port.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To view instance information for a receive port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to view instance information for a receive port.  
  
3. Click **Receive Ports**, select the receive port, click **View**, and then click **Instance Information**.  
  
    The query results panel in the lower section of the page displays all instances of the receive port.  
  
4. To refine the query and view different instance information for the receive port, click the box under **Value** for the **Search For** field, select the instance type to view, and then click **Run Query**. For more information about creating queries, see the topics on searching under See Also.  
  
## See Also  
 [Managing Receive Ports](../core/managing-receive-ports.md)   
 [How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md)   
 [How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md)   
 [How to Search for Messages](../core/how-to-search-for-messages.md)   
 [How to Search for Subscriptions](../core/how-to-search-for-subscriptions.md)