---
description: "Learn more about: Receive Oracle Database change notifications on multiple receive locations"
title: "Receive Oracle Database change notifications on multiple receive locations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d273517-9527-4208-99be-97c8a92f176d
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Oracle Database change notifications on multiple receive locations
Consider a scenario where you have multiple receive locations created as part of different BizTalk applications configured to receive query notifications for the same table (e.g. ACCOUNTACTIVITY) in the same database. If a hundred records are inserted into the same table, all the receive locations will get the notification message. To effectively receive notifications across multiple receive locations, you can call operations from your BizTalk application in such a way that if a notification is received by one receive location, the other receive location does not get the same notification. So, you can effectively load-balance notifications received on multiple locations.

 The tasks required to set up an orchestration to load-balance receiving notifications are same as that for [Receiving Oracle Database Change Notifications Incrementally Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md). This topic lists the only the difference between the two approaches.

## Load-Balancing Query Notifications Across Multiple Receive Locations
 Like in the topic [Receiving Oracle Database Change Notifications Incrementally Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md), you configured incremental notifications by executing a PROCESS_RECORDS procedure. To configure load-balancing, you could execute a stored procedure that deletes the records that have been notified for. For example, consider a stored procedure NOTIFY_LOAD_BALANCE with the following definition:

```
PROCEDURE NOTIFY_LOAD_BALANCE (TABLE_DATA OUT SYS_REFCURSOR) IS
  var int;
BEGIN
  SELECT TID INTO var FROM ACCOUNTACTIVITY WHERE ROWNUM = 1 FOR UPDATE;
  OPEN TABLE_DATA FOR SELECT * FROM ACCOUNTACTIVITY WHERE TID = var;
  DELETE FROM ACCOUNTACTIVITY WHERE TID = var;
END NOTIFY_LOAD_BALANCE;
```

 When you execute this stored procedure as part of the BizTalk application, the record for which notification is already received gets deleted. So, the other receive location gets notification for the next record.

 Here are the high-level steps you must perform to configure load-balancing for receiving notifications.

1. Create schema for **Notification** (inbound operation) and **NOTIFY_LOAD_BALANCE** procedure (outbound operation).

2. Add an orchestration and add three messages for receiving notification, executing the procedure, and getting response for the procedure.

3. Create an orchestration by adding Send and Receive shapes, Construct Message shape, and ports. You can use the same sample code for constructing a message to invoke the NOTIFY_LOAD_BALANCE stored procedure. Note that while performing the operation in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must have the request message for the NOTIFY_LOAD_BALANCE procedure in the location C:\TestLocation\MessageIn. You do so because the code snippet you invoke as part of the orchestration created in [Receiving Oracle Database Change Notifications Incrementally Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md) creates a request message based on the request XML present in C:\TestLocation\MessageIn.

4. Build and deploy the application. To demonstrate load-balancing, you must deploy this orchestration at least on two different computers that have [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] installed.

5. In the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console on both the computers, specify the following binding properties for the WCF-Custom or WCF-OracleDB receive location:


   |     Binding Property      |                                                                                                                                                                                                                                                                         Value                                                                                                                                                                                                                                                                         |
   |---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **InboundOperationType**  |                                                                                                                                                                                                                                                             Set this to **Notification**.                                                                                                                                                                                                                                                             |
   |   **NotificationPort**    | Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database. Set this to the same port number that you must have added to the Windows Firewall exceptions list. For instructions on how to add ports to Windows Firewall exceptions list, see [https://go.microsoft.com/fwlink/?LinkID=196959](/previous-versions/orphan-topics/ws.11/cc753558(v=ws.11)). **Important:**  If you set this to the default value of -1, you will have to completely disable Windows Firewall to receive notification messages. |
   | **NotificationStatement** |                                                                                                                                                                 Set this to:<br /><br /> `SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’` **Note:**  You must specify the table name along with the schema name. For example, `SCOTT.ACCOUNTACTIVITY`.                                                                                                                                                                 |
   | **NotifyOnListenerStart** |                                                                                                                                                                                                                                                                 Set this to **True**.                                                                                                                                                                                                                                                                 |


6. Start the BizTalk application.

7. To start receiving notifications, insert a hundred records into the ACCOUNTACTIVITY table. While doing so, make sure the request XML for invoking the NOTIFY_LOAD_BALANCE procedure is available in C:\TestLocation\MessageIn.

8. Monitor the location (on both the computers) where the BizTalk application will be dropping the notification messages. You will notice that of the hundred records inserted, one location gets notifications for some records while the other location gets notification for the remaining records. Together, both the locations will get notification for all the hundred records.

## See Also
 [Receiving Oracle Database Change Notifications Incrementally Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md)