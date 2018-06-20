---
title: "Considerations for Receiving Query Notifications Using the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0142f385-3d55-41a7-a50e-dda94b96d0a4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations for Receiving Query Notifications Using the SQL adapter
This topic provides some considerations and best practices to keep in mind while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive query notifications from a SQL Server database.  
  
## Considerations While Using the Adapter to Receive Notifications  
 You must consider the following while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive query notifications:  
  
- The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] receives the query notification from SQL Server, and then simply passes on the notification to the adapter clients. The adapter does not distinguish between the notifications for different operations (i.e., the adapter does not have any information whether a particular notification is for an Insert operation or an Update operation).  
  
- The notification message for an operation is not affected by the number of records affected by that operation. For example, regardless of the number of records inserted, updated, or deleted in a SQL Server database table, the adapter client receives only one notification message.  
  
- We recommend that the adapter client application contain the logic to interpret the type of notification received from SQL Server. The notification type can be determined by extracting the information from, the **\<Info\>** element of the received notification message. Here’s an example of a notification message received for an Insert operation:  
  
  ```  
  <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
    <Info>Insert</Info>  
    <Source>Data</Source>  
    <Type>Change</Type>  
  </Notification>  
  ```  
  
   Notice the value within the **\<Info\>** element. This value provides information on the operation for which the notification message was received. Your application should have the functionality to extract the value within the **\<Info\>** element and then based on the value, perform subsequent tasks. The topic [Process Notification Messages to complete Specific Tasks in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md) has instructions on how to extract the value within the **\<Info\>** element. A detailed tutorial that performs similar tasks is also available at [Tutorial 2: Employee - Purchase Order Process using the SQL adapter](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).  
  
- Ideally, after the client application receives a notification for a specific record, that record should be updated so that additional notifications are not received. For example, consider an **Employee** table that has a **Status** column. For all new records inserted into the **Employee** table, the value in the **Status** column is always “0” so the table will look like the following:  
  
  |Employee Name|Status|  
  |-------------------|------------|  
  |John|0|  
  
   To receive notifications for the newly inserted record, the adapter client will set the **NotificatonStatement** binding property as:  
  
  ```  
  SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0  
  ```  
  
  > [!NOTE]
  >  You must specifically specify the column names in the statement as shown in this SELECT statement. Also, you must always specify the table name along with the schema name. For example, dbo.Employee.  
  
   After receiving the notification, the client application must reset the value of the **Status** column to “1” so that the notification statement does not operate on the record again. To achieve this, the client application must perform an Update operation on the **Employee** table. After the Update operation, the same record in the **Employee** table will look like the following:  
  
  |Employee Name|Status|  
  |-------------------|------------|  
  |John|1|  
  
   Interestingly, the Update operation will again send a notification to the adapter client and the whole process will be repeated again, therefore, the client application must have the required logic to discard such unwanted notifications.  
  
- If the **NotifyOnListenerStart** binding property is true, the adapter client will receive a notification message every time the receive location starts. For more information on how to use the binding property and interpret the notification message, see [Receive Query Notifications After a Receive Location Breakdown in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-after-a-sql-receive-location-stops-in-biztalk.md).  
  
## Typical Orchestration for Receiving Notifications  
 This section outlines the typical orchestration flow for receiving notifications using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
1. The first thing that the orchestration must do is to determine the type of notification received, including:  
  
   - Whether the notification was received after a receive location restarts.  
  
   - Whether the notification was received for an operation on a database table, such as Insert, Update, or Delete.  
  
     The orchestration must include an **Expression** shape, and within that, an xpath query to decide what kind of message is received.  
  
2. After the notification type is determined, the orchestration must include a decision block to perform specific actions based on the type of notification received. To achieve this, the orchestration must include a **Decide** shape, which includes a **Rule** block and an **Else** block:  
  
   -   Within the **Rule** block, you must specify the condition and then include orchestration shapes to perform certain operations if the condition is met.  
  
   -   Within the **Else** block, you must include orchestration shapes to perform certain operations if the condition is *not* met.  
  
   Details of the preceding requirements are described in [Process Notification Messages to complete Specific Tasks in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md). A detailed tutorial is also available in [Tutorial 2: Employee - Purchase Order Process using the SQL adapter](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).