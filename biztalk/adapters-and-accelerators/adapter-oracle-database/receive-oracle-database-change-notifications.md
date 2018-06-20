---
title: "Receive Oracle Database Change Notifications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ffabf27-7223-4473-b33e-af6f2990cb96
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Oracle Database Change Notifications
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports the ODP.NET Database Change Notification feature. Using this feature, the adapter clients can register a SELECT statement as the notification query on the database, and the database sends a notification to the adapter client as and when the result set of the SELECT statement changes. The database change notification is implemented in the adapter using the OracleDependency class. For more information about the Database Change Support feature in ODP.NET and the OracleDependency class, see [http://go.microsoft.com/fwlink/?LinkId=124801](http://go.microsoft.com/fwlink/?LinkId=124801).  

 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes an inbound operation, Notification, to support database change notification. However, for the database change notification to work with [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must ensure the following:  

- Connect to the Oracle database with the underlying Oracle database version 10.2 or later. Oracle database versions prior to 10.2 do not support notifications.  

- Connect to Oracle database as a user that has the CHANGE NOTIFICATION privilege to create a notification registration. To grant the CHANGE NOTIFICATION privilege to a user, connect to the Oracle database as a user with administrative privileges, and run the following command at the SQL prompt:  

  ```  
  grant change notification to <user name>  
  ```  

- Decide on a TCP port that can be used by ODP.NET to receive database change notifications from Oracle database. Add the TCP port to Windows Firewall exceptions list. For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959). You must provide the same TCP port number for the **NotificationPort** binding property. For more information about the binding property, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx).  

  A typical database change notification using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] involves the following:  

1.  The adapter clients must specify `Notification` as the inbound operation in the **InboundOperationType** binding property. The default value for this binding property is Polling.  

2.  The adapter clients must specify a SQL SELECT statement to register for database change notifications in the **NotificationStatement** binding property. The adapter client gets a notification from Oracle database as and when the result set for the specified SQL statement changes.  

3.  The adapter clients must specify whether the adapter sends a notification to the adapter clients as soon as the listener is started in the **NotifyOnListenerStart** binding property.  

4.  The notification is sent to the adapter clients as and when the result set of the SELECT statement specified in the **NotificationStatement** binding property is changed.  

> [!CAUTION]
>  If there is a network outage between the Oracle database and the adapter client, the notifications will not be sent to the adapter clients for the changes done on the Oracle database during the period of network outage, and thereafter. Therefore, you must use the Polling operation instead of the Notification operation for critical scenarios.  

## Differences between Notification and Polling  
 Though notification and polling are both inbound operations, and inform the adapter clients about the data changes in the Oracle database, the following table illustrates some differences between the two. The following differences will help you decide on an operation depending on your requirements:  


|                                                                                                                              Notification                                                                                                                               |                                                                                                                                                                                                                                                      Polling                                                                                                                                                                                                                                                      |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                               Notification is supported only for Oracle database versions 10.2 and later.                                                                                               |                                                                                                                                                                          Polling is supported for all the Oracle database versions that are supported by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].                                                                                                                                                                           |
|                                                                                                          The data-change notification is always instantaneous.                                                                                                          | You can either configure the polling interval to check the data available for polling at regular intervals or instantaneously as and when the data is available. **Tip:**  Polling can give you better throughput in scenarios where the data changes are happening continuously, and you do not want to be notified of each change as and when it happens. Instead, you specify a polling interval after which you want to be notified of all the changes that have happened since the last change notification. |
| Notification is initiated by the Oracle database. The notification statement issued by the adapter just instructs the database to initiate notification in case there is a change in the result set of the statement. Notification is a feature of the Oracle database. |                                                                                                                                         Polling is initiated by the adapter. The adapter executes a SQL statement to validate whether data is available for polling, and then initiates polling by executing the polling statement if some data is available for polling.                                                                                                                                         |
|                                                                                             You can use the notification statement to only read data in an Oracle database.                                                                                             |                                                                                                                                                                                                                 You can use the polling statement to read or update data in the Oracle database.                                                                                                                                                                                                                  |
|                                                                                   Notification informs only about the type of change in the data such as Insert, Update, and Delete.                                                                                    |                                                                                                                                                                                                                            Polling informs you about the actual data that has changed.                                                                                                                                                                                                                            |

 For more information about:  

- The binding properties related to the Notification operation, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx).  

- How to use the Notification operation in [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Receiving Oracle Database Change Notifications Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md).  

## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)