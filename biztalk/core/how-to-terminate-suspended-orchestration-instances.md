---
title: "How to Terminate Suspended Orchestration Instances | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, terminating [HAT]"
  - "messages, saving [HAT]"
  - "HAT, saving messages"
  - "HAT, terminating pipelines"
  - "HAT, terminiating orchestrations"
  - "orchestrations, terminating [HAT]"
ms.assetid: b5d44cce-b05c-47f9-9015-5b10c2312bf1
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Terminate Suspended Orchestration Instances
You can terminate any suspended orchestration instances or ports from the Query results or preview pane in the BizTalk Server Administration Console.  
  
> [!NOTE]
>  Each instance of an ordered delivery a send port may have several messages associated with it. To prevent accidental termination or data loss, be sure you have reviewed all such associations before terminating an instance.  
  
## Prerequisites  
 You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.  
  
### To terminate suspended orchestration instances  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.  
  
3. In the details pane, click the **New Query** tab.  
  
4. In the **Query Expression** group, in the **Value** column, select **Suspended Service Instances** from the drop-down list box.  
  
5. Do one of the following:  
  
   - To terminate a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select the **Service Name</em>* filter and then in the **Value** column, specify the service name.  
  
   - To terminate instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select **Group Results By</em>* and then in the **Value** column, specify the service name.  
  
6. Click **Run Query**.  
  
7. In the query results list, right-click the orchestration instance or group of instances you want to terminate, and then click **Terminate Instance** or **Terminate Instances**.  
  
## See Also  
 [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md)