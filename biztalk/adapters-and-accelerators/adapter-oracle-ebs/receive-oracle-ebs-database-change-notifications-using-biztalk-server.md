---
title: "Receive Oracle E-Business Suite database change notifications using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e92520cf-c552-4225-abba-8e03f73ecf70
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Oracle E-Business Suite database change notifications using BizTalk Server
You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive database change notification messages from Oracle E-Business Suite. You can specify a SELECT statement that the adapter uses to register for notifications with Oracle E-Business Suite. The adapter receives a notification message when the result set for the SELECT statement, registered for notification, changes. For more information about how the adapter supports notification, see [Considerations for Receiving Database Change Notifications using the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md).  
  
 Following are some scenarios in which you can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to receive notifications from Oracle E-Business Suite:  
  
- Adapter clients get only “incremental” notification, for example, only for those changes that were made to a database table since the last notification.  
  
- If a large number of rows are inserted into a database table, the adapter clients can configure multiple receive locations to load-balance receiving notifications.  
  
  After the adapter clients receive a notification message, they can perform specific tasks based on the kind of notification received. For example, a BizTalk orchestration can be designed in such a way that it performs one set of tasks if an insert notification is received and another set of tasks if an update notification is received.  
  
> [!CAUTION]
>  If there is a network outage between the Oracle database and the adapter client, the notifications will not be sent to the adapter clients for the changes done on the Oracle database during the period of network outage, and thereafter. Therefore, you must use the Polling operation instead of the Notification operation for critical scenarios.  
  
 The topics in this section provide information on how to configure the adapter for each of these scenarios. To start getting notifications from Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must specify certain binding properties. For more information about the binding properties related to notifications, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). For more information about structure of notification messages, see [Message Schemas for the Notification Operation](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-notification-operation2.md).  
  
 For receiving notifications from Oracle E-Business Suite, make sure:  
  
-   You use the adapter to connect to a supported Oracle database version. Oracle database versions prior to 10.2 do not support notifications.  
  
-   The **change notification** privilege is required for receiving database change notifications.  To configure this privilege, connect to Oracle database using administrative privileges and then type the following command on the SQL prompt.  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   Decide on a TCP port you want ODP.NET to use for receiving database change notifications from Oracle database. Add that port to Windows Firewall exceptions list. For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959). You must provide the same port number for the **NotificationPort** binding property. For more information about the binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## In This Section  
  
-   [Considerations for Receiving Database Change Notifications using the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md)  
  
-   [Process Notification Messages to Complete Specific Tasks in Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)  
  
-   [Receive Oracle E-Business Suite Change Notifications Incrementally Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [Receive Oracle E-Business Suite database Change Notifications On Multiple Receive Locations](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [Receive Oracle E-Business Suite Database Change Notifications After a Receive Location Breakdown](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md)  
  
## See Also  
[Develop BizTalk applications using the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)