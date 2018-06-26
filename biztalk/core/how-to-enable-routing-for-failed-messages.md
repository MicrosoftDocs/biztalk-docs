---
title: "How to Enable Routing for Failed Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d33beed4-1ae2-4282-95ac-5d68aab7fb5d
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable Routing for Failed Messages
Failed message routing is a property of send and receive ports, and is enabled by indicating "Enable routing for failed messages" on the port's property page.  
  
> [!NOTE]
>  The configuration on a receive port applies to all receive locations associated with that receive port.  
  
> [!NOTE]
>  The configuration on a send port applies to both the primary and backup transports.  
  
### To configure failed message routing for a receive port (this applies to both one-way and request-response receive ports)  
  
1. Open the BizTalk Server Administration console.  
  
2. Expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application to which the send port belongs.  
  
3. Click the **Receive Ports** folder.  
  
4. In the right pane, double-click the name of the receive port you want to configure.  
  
5. On the receive port's property page, in the left pane, select the **General** category.  
  
6. In the right pane, select the **Enable routing for failed messages** check box, and then click **Apply**.  
  
### To configure failed message routing for a send port (this applies only to static one-way and static solicit-response send ports)  
  
1. Open the BizTalk Server Administration console.  
  
2. Expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application to which the send port belongs.  
  
3. Click the **Send Ports** folder.  
  
4. In the right pane, double-click the name of the send port you want to configure.  
  
5. On the send port's property page, in the left pane, select the **Transport Advanced Options** category.  
  
6. In the right pane, in the **Transport Options** group box, select the **Enable routing for failed messages** check box, and then click **Apply**.  
  
## See Also  
 [Error Handling](../core/error-handling.md)