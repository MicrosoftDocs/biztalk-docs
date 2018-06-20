---
title: "How to Suspend, Resume, and Terminate Orchestration Instances | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [orchestrations], resuming"
  - "orchestrations, terminating"
  - "managing [orchestrations], suspending"
  - "orchestrations, resuming"
  - "orchestrations, suspending"
  - "managing [orchestrations], terminating"
ms.assetid: 7b373dad-57d5-4696-9b29-a6c351d44fa8
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Suspend, Resume, and Terminate Orchestration Instances
This topic describes how to suspend, resume, and terminate one or more running service instances of an orchestration by using the BizTalk Server Administration console. A service instance is an instance of an orchestration that BizTalk Server is either processing or that has been serialized into the MessageBox for further processing or tracking.  
  
 The following describes the effects of these three operations:  
  
-   **Suspend.** This pauses the service instance. In-process messages run to completion. Messages are still routed to service instances, but are not processed.  
  
-   **Resume.** This resumes processing of suspended instances.  
  
> [!NOTE]
>  You cannot resume an instance from a breakpoint state. Resuming such an instance may show a status of "Pending," but the instance will eventually fail.  
  
-   **Terminate.** This terminates all message processing. The service instance is deleted from the BizTalk Server databases. Messages that the service instance is processing are also deleted, except for any messages that are also referenced by a service instance that is not being terminated.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Operators group or the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To view start, stop, or terminate an instance of an orchestration  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. Select the BizTalk Group to display the Group Hub page.  
  
3. Under **Work in Progress**, click **Running service instances**.  
  
    The query results panel in the lower section of the page displays all instances of the orchestration.  
  
4. To refine the query and view different instances for the orchestration, click the box under **Value** for the **Search For** field, select the instance type to view, and then click **Run Query**. For more information about creating queries, see the topics on searching under See Also.  
  
5. Right-click the instance you want and click **Suspend**, **Resume**, or **Terminate**. This functionality allows you to select which instances to resume.  
  
   > [!NOTE]
   >  To perform the operation on multiple instances, hold down the CTRL key and click the instances you want. Then right-click an instance and click **Suspend**, **Resume**, or **Terminate**.  
  
    [Service Instance States](../core/service-instance-states.md) provides more information on the suspended state.  
  
## See Also  
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md)   
 [How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md)