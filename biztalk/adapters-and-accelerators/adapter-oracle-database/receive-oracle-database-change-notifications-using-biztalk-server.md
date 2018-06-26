---
title: "Receive Oracle Database Change Notifications Using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 495a29bc-72f6-4140-8160-0b917d935503
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Oracle Database Change Notifications Using BizTalk Server
You can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive database change notification messages from the Oracle database. You can specify a SELECT statement that the adapter uses to register for notifications with the Oracle database. The adapter receives a notification message when the result set for the SELECT statement, registered for notification, changes. For more information about how the adapter supports notification, see [Considerations for Receiving Database Change Notifications using the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md).  
  
 Following are some scenarios in which you can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to receive notifications from the Oracle database:  
  
- Adapter clients get only “incremental” notification, for example, only for those changes that were made to a database table since the last notification.  
  
- If large number of rows are inserted into a database table, the adapter clients can configure multiple receive locations to load-balance receiving notifications.  
  
  Once the adapter clients receive a notification message, they can perform specific tasks based on the kind of notification received. For example, a BizTalk orchestration can be designed in such a way that it performs one set of tasks if an insert notification is received and another set of tasks if an update notification is received.  
  
> [!CAUTION]
>  If there is a network outage between the Oracle database and the adapter client, the notifications will not be sent to the adapter clients for the changes done on the Oracle database during the period of network outage, and thereafter. Therefore, you must use the Polling operation instead of the Notification operation for critical scenarios.  
  
 The topics in this section provide information on how to configure the adapter for each of these scenarios. To start getting notifications from the Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must specify certain binding properties. For more information about the binding properties related to notifications, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx). For more information about structure of notification messages, see [Message Schemas for the Notification Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md).  
  
 For receiving notifications from the Oracle database, make sure:  
  
-   You use the adapter to connect to Oracle database version 10.2 or later. Oracle database versions prior to 10.2 do not support notifications.  
  
-   The credentials you use to connect to Oracle for notifications has `change notification` privilege. This privilege is required for receiving database change notifications. To do so, connect to Oracle database using administrative privileges and then type the following command on the SQL prompt.  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   Decide on a TCP port you want ODP.NET to use for receiving database change notifications from Oracle database. Add that port to Windows Firewall exceptions list. For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959). You must provide the same port number for the **NotificationPort** binding property. For more information about the binding property, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx).  
  
## In This Section  
  
-   [Considerations for Receiving Database Change Notifications Using the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [Processing Notification Messages to Complete Specific Tasks in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)  
  
-   [Receiving Oracle Database Change Notifications Incrementally Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [Receiving Oracle Database Change Notifications On Multiple Receive Locations](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [Receiving Oracle Database Change Notifications After a Receive Location Breakdown](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-after-a-receive-location-breakdown.md)  
  
## See Also  
[Building Blocks to Develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)