---
title: "How to Resume Suspended Orchestration Instances | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instances, resuming [HAT]"
  - "HAT, resuming orchestrations"
  - "HAT, resuming pipelines"
  - "orchestrations, resuming"
  - "resuming, pipelines"
  - "resuming, orchestrations"
  - "HAT, debug mode"
ms.assetid: da133183-68d9-48d1-9601-8f6d4d5b8898
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Resume Suspended Orchestration Instances
If you have suspended orchestration instances that are listed as "suspended resumable," you can attempt to resume the orchestration instance from the query results or preview pane. Resuming the orchestration instance will only succeed if the underlying problem that caused the orchestration instance to become suspended has also been fixed.  
  
## Prerequisites  
 You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.  
  
### To resume suspended orchestration instances  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.  
  
3. In the details pane, click the **New Query** tab.  
  
4. In the **Query Expression** group, in the **Value** column, select **Suspended Service Instances** from the drop-down list box.  
  
5. Do one of the following:  
  
   - To resume a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select the **Service Name</em>* filter and then in the **Value** column, specify the service name.  
  
   - To resume instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select **Group Results By</em>* and then in the **Value** column, specify the service name.  
  
6. Click **Run Query**.  
  
7. In the query results list, right-click the orchestration instance you want to resume, and then click **Resume Instance** or **Resume Instances**. This allows you to select which instances to resume.  
  
    [Service Instance States](../core/service-instance-states.md) provides more information on the on the suspended state.  
  
## See Also  
 [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md)
