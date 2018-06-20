---
title: "How to Control the Size of the Results List | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "results list [Orchestration Debugger], deleting columns"
  - "results list [Orchestration Debugger], limiting list size"
  - "Orchestration Debugger, results list"
  - "results list [Orchestration Designer]"
  - "results list [Orchestration Debugger], adding columns"
ms.assetid: 4d41003f-5ea9-4599-8ec0-737c342ffdbd
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Control the Size of the Results List
On the **Group Hub** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, the Query results pane contains so many columns of information that you need to scroll to view them. You can add or remove columns in the pane to display only the information that you need. To add or remove columns, right-click any part of the Query results pane and click **Add/Remove Columns** on the context menu.  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.  

### To add or remove columns in the results list  

1. Right-click any cell in the **Query results** list, and then click **Add/Remove Columns** on the context menu.  

   > [!NOTE]
   >  Items that are already present in the results list appear on the right side under **Displayed Columns**. Items that are not present in the results list appear on the left side under **Available Columns**.  

2. To add a column, select one of the items from **Available Columns** and click **Add** to move that column to the list of **Displayed Columns**.  

3. To remove a column, select one of the items from **Displayed Columns** and click **Remove** to move that column to the list of **Available Columns**.  

   You can control the number of results that the query returns by using the filters that are provided when you create or run a query.  

## Columns in the Query Results List  
 The query results are displayed in the Query results pane at the bottom of the view that originated the query. You cannot directly access the results list. The context menu shows all of the actions you can perform on the selected record within the currently active view. For example, if the record contains a Service Instance ID, then service-related actions appear. If there is a Message ID, then message-related actions appear.  

 Because you might not need all the information contained in this complete list, you can select only those columns you want to view, or you can replace columns that you removed. When you sort the results list by time, the instances sort up to milliseconds, even if no milliseconds appear on the list. When you reuse a saved query the results show only the columns selected each time the query is run.  

 The following table shows a complete list of the items that appear in the results list.  


|                              |                                                                                                                                           |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **Service or Message field** |                                                              **Description**                                                              |
|         Service Name         |                                                       Name of the service instance.                                                       |
|          Event Type          |                    Type of service (for example, messaging (reported as Pipeline), orchestration, transport adapter).                     |
|      Error Description       |                                                 Description of the error if one occurred.                                                 |
|            State             |                                              State of the operation when the query was run.                                               |
|          Error Code          |                                                    Code of the error if one occurred.                                                     |
|    Decryption Certificate    |                                   Shows the certificate information relating to the message or service.                                   |
|           Duration           |                                                    Time for the operation to complete.                                                    |
|          Port Name           |                                                Port involved in the flow of the instance.                                                 |
|          Signature           |                                               Digital signature information of the message.                                               |
|             Size             |                                                       Size of the message in bytes.                                                       |
|          Start Time          |                                                        Time the operation started.                                                        |
|           End Time           |                                                         Time the operation ended.                                                         |
|          Part Count          |                                                      Number of parts in the message.                                                      |
|            Party             |                                              Identifier of the party starting the operation.                                              |
|             URI              |                                                       URI of the initiating party.                                                        |
|          TimeStamp           |                                                        Time the operation started.                                                        |
|             Host             |                                          Name of the BizTalk Host running the service instance.                                           |
|        Assembly Name         |                                      Name of the .NET assembly that implements the service instance.                                      |
|       Assembly Version       |                                                  Version number of the related assembly.                                                  |
|       Deployment Time        | Time that the service instance assembly deployed into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. |
|         Activity ID          |     Identifies unique service instance activity (for example, messages sent/received by the pipeline/orchestration have the same ID).     |
|     Service Instance ID      |                              Globally unique identifier (GUID) that identifies a run of a service instance.                               |
|     Message Instance ID      |                                   Globally unique identifier (GUID) that identifies a message instance.                                   |
|          Service ID          |                                       Globally unique identifier (GUID) that identifies a service.                                        |
|        Service Class         |                                                Type of class (pipeline or orchestration).                                                 |
|       Service Class ID       |                            A service-independent GUID that identifies a service (for example, orchestration).                             |
|             Icon             |                                                          Icon of the result row.                                                          |
|           Adapter            |                                                      Adapter used in the operation.                                                       |

