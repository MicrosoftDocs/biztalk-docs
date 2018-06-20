---
title: "How to Suspend Orchestration Instances or Ports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipelines, suspending"
  - "instances, suspending"
  - "suspending"
  - "HAT, suspending orchestrations"
  - "HAT, suspending pipelines"
  - "suspending, ports"
  - "suspending, orchestrations"
  - "orchestrations, suspending"
  - "HAT, suspending ports"
  - "suspending, instances"
  - "ports, suspending"
ms.assetid: cacc7e58-7d3e-4d6b-adb0-618fdc4f0d89
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Suspend Orchestration Instances or Ports
You can suspend orchestration instances or ports from a query results list in the BizTalk Server Administration Console.  
  
## Prerequisites  
 You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.  
  
### To suspend orchestration instances or ports  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.  
  
3. In the details pane, click the **New Query** tab.  
  
4. In the **Query Expression** group, in the **Value** column, select **Running Service Instances** from the drop-down list box.  
  
5. Do one of the following:  
  
   - To suspend a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select the **Service Name</em>* filter and then in the **Value** column, specify the service name.  
  
   - To suspend instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select **Group Results By</em>* and then in the **Value** column, specify the service name.  
  
6. Click **Run Query**.  
  
7. In the query results list, right-click the active orchestration or port you want to suspend, and then click **Suspend Instance** or **Suspend Instances**.  
  
## See Also  
 [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md)