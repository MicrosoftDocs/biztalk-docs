---
title: "How to Search for Suspended Service Instances | Microsoft Docs"
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
  - "service instances, suspended"
  - "Query tab [Administration Console], searching"
  - "instances, suspended"
  - "instances, services"
ms.assetid: f91b1151-d879-4aa7-afc8-4cf13d928158
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Search for Suspended Service Instances
You can use the **Query** tab in the BizTalk Server Administration Console to search for suspended service instances. You can search for a specific subset of messages to locate a specific message associated with a service name, type, host, etc.  

> [!NOTE]
>  Terminated w/ unconsumed message instances are displayed as an error code (“Terminated with unconsumed messages”) for the pertinent suspended service instances. These instances are non-resumable.  

> [!NOTE]
>  When Grouping and Filtering by URI or error adapter name, only send and receive ports are displayed in the results. Grouping and Filtering by URI is not possible for orchestrations, which are not included in the displayed results.  

## Prerequisites  
 To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.  

### To search for suspended service instances  

1. Click **Start**, click **All Programs**, click **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.  

3. In the details pane, click the **New Query** tab.  

4. In the **Query Expression** group, in the **Value** column, select **Suspended Service Instances** from the drop-down list box.  

5. In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\***), select one or more of the following:  


   |         Item          |                                                                                                                                                                                                                   Description                                                                                                                                                                                                                   |
   |-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Application Name**  |                                                                                                                                                                                                   The name of the BizTalk Server application.                                                                                                                                                                                                   |
   |   **Creation Time**   |                                                                                                                                                                                  Find suspended service instances created before or after the specified date.                                                                                                                                                                                   |
   |   **Error Adapter**   | You can group or filter suspended service instances by adapter type. For example: FILE, FTP, HTTP, MQSeries, MSMQ, POP3, SMTP, SOAP,  or Windows SharePoint Services. **Note:**  In the query results, the adapter field is only populated when the BizTalk Server runtime runs into an error while using the specified adater. If the runtime does not find an error with the adapter, in the query results, the Error Adapter field is empty. |
   |    **Error Code**     |                                                                                                                                                 You can group or filter suspended service instances by error code to show all that service instances have been suspended with that error code.                                                                                                                                                  |
   | **Error Description** |                                                                                                                                                                            You can group or filter suspended service instances with the specified error description.                                                                                                                                                                            |
   | **Group Results By**  |                                                                                                                                        You can group or filter results by adapter, application, error code, error description, host name, service class, service instance status, service name, or URI.                                                                                                                                         |
   |     **Host Name**     |                                                                                                                                                                                            Group or filter suspended service instances by host name.                                                                                                                                                                                            |
   |  **Instance Status**  |                                                                                                                                                                         You can search for suspended but not resumable instances, or suspended and resumable instances.                                                                                                                                                                         |
   |  **Maximum Matches**  |                                                                                                                                                                                                        The number of matches to display.                                                                                                                                                                                                        |
   |   **Service Class**   |                                                                                                                                                       You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report.                                                                                                                                                       |
   |   **Service Name**    |                                                                                                                                                                                      You can group or filter suspended service instances by service name.                                                                                                                                                                                       |
   |  **Service Type ID**  |                                                                                                                                                                                     You can group or filter suspended service instances by service type ID.                                                                                                                                                                                     |
   |  **Suspension Time**  |                                                                                                                                                                        You can group or filter suspended service instances suspended before or after the specified date.                                                                                                                                                                        |
   |        **URI**        |                                              You can group or filter suspended service instances by URI. **Note:**  In the query results, the URI is only populated when the BizTalk Server runtime runs into an error while sending to the specified URI. If the runtime does not find an error when sending to the URI, in the query results, the URI field is empty or shows "URI unavailable."                                              |


6. Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.  

7. Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.  

## See Also  
 [Using the Administration Console Query Tab](../core/using-the-administration-console-query-tab.md)