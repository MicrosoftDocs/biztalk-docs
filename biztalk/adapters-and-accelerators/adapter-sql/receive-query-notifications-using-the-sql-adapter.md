---
title: "Receive query notifications using the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b2ed0f0-d005-4eec-b1a6-97a0c94678dc
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive query notifications using the SQL adapter
The adapter clients can subscribe to receive query notifications about the data changes in the SQL Server database. A SQL SELECT statement or a stored procedure specifies the data-change criteria in a table for triggering of the query notifications, and the SQL Server sends query notifications as and when the result set for the SELECT statement or the stored procedure changes.  
  
> [!IMPORTANT]
>  To support query notifications, the adapter clients and the SQL Server database have to fulfill certain requirements. For detailed information about these requirements, see “Enabling Query Notifications” at [http://go.microsoft.com/fwlink/?LinkID=122323](http://go.microsoft.com/fwlink/?LinkID=122323).  
  
 A typical query notification involves the following:  
  
- The adapter clients must specify `Notification` as the inbound operation in the **InboundOperationType** binding property. The default value for this binding property is `Polling`.  
  
- The adapter clients must specify a SQL statement to register for query notifications in the **NotificationStatement** binding property. The adapter client gets a notification from SQL Server as soon as the result set for the specified SQL statement changes.  
  
  > [!IMPORTANT]
  >  To receive notifications, the SQL statement for the notification subscription *must* meet certain criteria. For information about SQL statements that can be used for query notifications, see [http://go.microsoft.com/fwlink/?LinkId=122160](http://go.microsoft.com/fwlink/?LinkId=122160).  
  
- The adapter clients must specify whether the adapter sends a notification to the adapter clients as soon as the listener is started in the **NotifyOnListenerStart** binding property.  
  
- The notification is sent to the adapter clients as and when the result set of the SQL statement specified in the **NotificationStatement** binding property is changed.  
  
  For more information about these binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
> [!NOTE]
>  The notification subscription is always committed, regardless of whether the transaction in which the statement ran was committed or rolled back. Therefore, the notification operation might not guarantee that the result of the query subscribed for notification has changed. For example, suppose data is inserted in a table row (subscribed for notification) in a transaction, and immediately a notification is sent to the adapter informing about the change (insert). Due to some reason, the transaction rolls back, and effectively no data is inserted into the table row. However, the SQL Server does not send a notification to the adapter about the transaction roll back. For information about query notifications in SQL Server, see [http://go.microsoft.com/fwlink/?LinkId=145367](http://go.microsoft.com/fwlink/?LinkId=145367).  
  
## Differences between Query Notification and Polling  
 Though query notification and polling are both inbound operations, and inform the adapter clients about the data changes in the SQL Server database, the following table lists some differences between the two. The following differences will help you decide on an operation depending on your requirements:  
  
|Query Notification|Polling|  
|------------------------|-------------|  
|Query notification is initiated by SQL Server. The notification statement issued by the adapter just instructs the database to initiate notification in case there is a change in the result set of the statement.|Polling is initiated by the adapter. The adapter executes a statement to validate whether data is available for polling, and then initiates polling by executing the polling statement if some data is available for polling.|  
|You can use the query notification statement to only read data in a SQL Server database table.|You can use the polling statement to read or update data in a SQL Server database table.|  
|Query notification informs only about the type of change in the data such as Insert, Update, and Delete.|Polling informs you about the actual data that has changed.|  
|The data-change notification is instantaneous.|The data-change notification depends on the polling interval, and the adapter clients are informed about the data changes at the end of every polling interval. **Tip:**  Polling can give you better throughput in scenarios where the data changes are happening continuously, and you do not want to be notified of each change as and when it happens. Instead, you specify a polling interval after which you want to be notified of all the changes that have happened since the last change notification.|  
  
 For more information about query notification in [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)], see [Receive SQL Query Notifications by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)