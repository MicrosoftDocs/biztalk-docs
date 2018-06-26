---
title: "Receive SQL Query Notifications using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69444df7-f2ae-4d1a-9b49-817b437517d8
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive SQL Query Notifications using BizTalk Server
You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive notification messages for SQL Server tables or views. You can specify a SQL statement that the adapter uses to register for notifications with SQL Server. The notification statement can be a SELECT statement or a stored procedure that returns a result set. For more information about query notifications, see “Using Query Notifications” at  [http://go.microsoft.com/fwlink/?LinkId=122159](http://go.microsoft.com/fwlink/?LinkId=122159). For information about queries that can be used for query notifications, see “Creating a Query for Notification” at [http://go.microsoft.com/fwlink/?LinkId=122160](http://go.microsoft.com/fwlink/?LinkId=122160).  
  
 Receiving query notifications from SQL Server is similar to polling SQL Server, with a few key differences. For the list of differences, see [Considerations Receiving Query Notifications Using the SQL adapter](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md).  
  
 Following are some scenarios in which you can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to receive notifications from SQL Server:  
  
- Adapter clients get only “incremental” notification, for example, only for those changes that were made to a database table since the last notification.  
  
- If many rows are inserted into a database table, the adapter clients can configure multiple receive locations to load-balance receiving notifications.  
  
- If the receive location on which the adapter clients are receiving notifications goes down, the adapter clients can configure the adapter to receive a notification as soon as the receive location is up again. The clients must also implement the logic in their application to process the records that may have been inserted, updated, or deleted while the receive location was down.  
  
  Once the adapter clients receive a notification message, they can perform specific tasks based on the kind of notification received. For example, a BizTalk orchestration can be designed in such a way that it performs one set of tasks if an insert notification is received and another set of tasks if an update notification is received.  
  
  The topics in this section provide information about how to configure the adapter for each of these scenarios. To start getting notifications from SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must specify certain binding properties. For more information about how the adapter supports receiving messages, see [Considerations Receiving Query Notifications Using the SQL adapter](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md). For more information about the binding properties related to notifications, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). For more information about the structure of notification messages, see [Message Schemas for Query Notification](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md).  
  
  You must also perform the following tasks on SQL Server to enable query notifications.  
  
- You must enable Service Broker for the SQL Server database.  
  
- You must ensure that the adapter client has the necessary permissions to execute commands to request notification.  
  
  For more information about these tasks, see “Enabling Query Notifications” at [http://go.microsoft.com/fwlink/?LinkID=122323](http://go.microsoft.com/fwlink/?LinkID=122323).  
  
## In This Section  
  
-   [Considerations Receiving Query Notifications Using the SQL adapter](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)  
  
-   [Process Notification Messages to complete Specific Tasks in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)  
  
-   [Receive Query Notifications Incrementally from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md)  
  
-   [Receive Query Notifications On Multiple Receive Locations from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-on-receive-locations-from-sql-server-using-biztalk.md)  
  
-   [Receive Query Notifications After a Receive Location Breakdown in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-after-a-sql-receive-location-stops-in-biztalk.md)  
  
## See Also  
[Develop BizTalk applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)