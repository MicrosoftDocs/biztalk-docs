---
title: "How to Search for Running Service Instances | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service instances, viewing"
  - "service instances, Query tab [Administration Console]"
  - "Query tab [Administration Console], service instances"
  - "Query tab [Administration Console], searching"
  - "service instances, searching"
  - "service instances, running"
ms.assetid: fc65bf33-c013-4e6a-b9fd-b4536811e7b4
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Search for Running Service Instances
You can use the **Query** tab in the BizTalk Server Administration Console to search for a specific dehydrated, active, in breakpoint, scheduled, and retrying service instance.  

## Prerequisites  
 To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.  

### To search for running service instances  

1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.  

3. In the details pane, click the **New Query** tab.  

4. In the **Query Expression** group, in the **Value** column, select **Running Service Instances** from the drop-down list box.  

5. In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\***), select one or more of the following:  


   |          Item          |                                                             Description                                                             |
   |------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
   |  **Application Name**  |                                                   The BizTalk Server application.                                                   |
   |   **Creation Time**    |                             Find running service instances created before or after the specified date.                              |
   |  **Group Results By**  |  You can group results by application, host name, pending operation type, service class, service instance status, or service name.  |
   |     **Host Name**      |                                                    The name of the BizTalk Host.                                                    |
   |  **Instance Status**   |             You can search for active instances, dehydrated instances, ready to run instances, and scheduled instances.             |
   |  **Maximum Matches**   |                                                  The number of matches to display.                                                  |
   | **Pending Operations** |                      You can search for running service instances that are pending suspension or termination.                       |
   |   **Service Class**    | You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report. |
   |    **Service Name**    |                                 You can group or filter running service instances by service name.                                  |
   |  **Service Type ID**   |                                        You can group or filter messages by service type ID.                                         |


6. Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.  

7. Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.  

## See Also  
 [Using the Administration Console Query Tab](../core/using-the-administration-console-query-tab.md)