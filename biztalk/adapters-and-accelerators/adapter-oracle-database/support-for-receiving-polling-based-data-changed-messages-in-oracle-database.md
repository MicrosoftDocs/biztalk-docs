---
title: "Support for Receiving Polling-based Data-changed Messages in Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "notifications, polling-based"
  - "post-polling"
  - "POLLINGSTMT"
  - "polling interval"
  - "polling"
ms.assetid: 9ff29d3f-ebb1-4d82-9106-150f939cbd9e
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Support for Receiving Polling-based Data-changed Messages in Oracle Database
The[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables client programs to receive messages from the Oracle database informing them of changes to data stored in an Oracle database. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports receiving "polling-based" messages wherein the adapter executes a specified SELECT query, stored procedure, function, or procedure or function within a package, retrieves the data, and provides the result to the client at regular intervals of time. To enable this, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes a POLLINGSTMT operation. Moreover, all the stored procedures, functions, and procedures and function within packages are exposed as inbound operations for polling.  

 The adapter provides two ways of polling the Oracle database:  

-   **Using SELECT statements**. You can specify a simple SELECT statement to poll the tables and views in the Oracle database. The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.  

-   **Using stored procedures, functions, or procedures or functions within a package**. You can specify a stored procedure, function, or procedure or function within a package to poll the Oracle database. The adapter executes the request message at specified intervals and returns the result to the adapter clients.  

## Polling Operation Workflow  
 A typical polling operation using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] involves the following:  

1. The adapter clients must specify **Polling** as the inbound operation in the **InboundOperationType** binding property. The default value for this binding property is **Polling**.  

2. The adapter clients must specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine whether there is data available for polling. On execution of this statement, if the first column of the first row of the result set returned contains a positive integer value, there is date available for polling. By default, the value of this binding property is set to `Select 1 FROM DUAL`, which implies that the adapter must continue polling irrespective of whether the table being polled has data or not.  

3. The adapter clients must specify a polling interval for the **PollingInterval** binding property to define the interval in seconds at which the statement specified in the **PolledDataAvailableStatement** binding property is executed. At the end of every polling interval, the polled data available statement is executed, and the result set is returned.  

4. The adapter clients must specify a SELECT statement or a stored procedure for the **PollingStatement** binding property.  

   - If you want to poll a table or view, you must specify a SELECT query in this binding property.  

   - If you want to poll using a stored procedure, function, or procedure or function within a package, you must specify the entire request message for the respective operation in this binding property.  

     The statement in the **PollingStatement** binding property is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property in step 1.  

5. The adapter clients must specify an action for the polling operation in the **PollingAction** binding property. The polling action for a specific operation is determined from the metadata generated for the operation using the Consume Adapter Service Add-in.  

   > [!NOTE]
   >  If you are polling a table or view using a SELECT statement in the **PollingStatement** binding property, you do not need to specify any value for the **PollingAction** binding property. The default value, Null, is passed in this case.  

6. The adapter clients can use the **PollWhileDataFound** binding property to ignore the polling interval, and continuously poll data, as and when available.  

   > [!IMPORTANT]
   >  If you set the value of the **PollWhileDataFound** binding property to True, the adapter clients continuously poll data from Oracle and in the process open and close connections to the Oracle database in a loop. As the rate at which connections are opened by ODP.NET is greater than the connections being closed, the connections get exhausted after some time, and an exception is thrown. As a work around, make sure that the value of the **UseOracleConnectionPool** is set to True, and an appropriate value is mentioned in the **IncrPoolSize** binding property to control the number of connections that can be opened by the adapter clients.  

7. The adapter clients can specify a post-poll statement, an Oracle PL/SQL block, for the **PostPollStatement** binding property. The statement specified in this binding property is executed after the statement specified in the **PollingStatement** binding property is executed.  

   The adapter wraps the polling statement and the post-poll statement in a transaction and the transaction timeout value is set as the value specified for the **PollingInterval** binding property. Therefore, it is critical to specify a timeout value that is greater than or equal to the time required to process the incoming message and send a reply. If the time taken by the client program to consume the message or execute the post-poll query is more than the timeout value, the transaction is rolled back. If the time taken is less than the timeout value, the adapter commits the transaction and "sleeps" for the remaining time in the poll before performing the next poll.  

   The adapter suppresses any empty polling responses coming from the Oracle database.  

## Differences between Polling and Notification  
 Though polling and notification are both inbound operations, and inform the adapter clients about the data changes in the Oracle database, the following table illustrates some differences between the two. The following differences will help you decide on an operation depending on your requirements:  


|                                                                                                                                                                                                                                                      Polling                                                                                                                                                                                                                                                      |                                                                                                                              Notification                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                                          Polling is supported for all the Oracle database versions that are supported by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].                                                                                                                                                                           |                                                                                               Notification is supported only for Oracle database versions 10.2 and later.                                                                                               |
| You can either configure the polling interval to check the data available for polling at regular intervals or instantaneously as and when the data is available. **Tip:**  Polling can give you better throughput in scenarios where the data changes are happening continuously, and you do not want to be notified of each change as and when it happens. Instead, you specify a polling interval after which you want to be notified of all the changes that have happened since the last change notification. |                                                                                                          The data-change notification is always instantaneous.                                                                                                          |
|                                                                                                                                         Polling is initiated by the adapter. The adapter executes a SQL statement to validate whether data is available for polling, and then initiates polling by executing the polling statement if some data is available for polling.                                                                                                                                         | Notification is initiated by the Oracle database. The notification statement issued by the adapter just instructs the database to initiate notification in case there is a change in the result set of the statement. Notification is a feature of the Oracle database. |
|                                                                                                                                                                                                                 You can use the polling statement to read or update data in the Oracle database.                                                                                                                                                                                                                  |                                                                                             You can use the notification statement to only read data in an Oracle database.                                                                                             |
|                                                                                                                                                                                                                            Polling informs you about the actual data that has changed.                                                                                                                                                                                                                            |                                                                                   Notification informs only about the type of change in the data such as Insert, Update, and Delete.                                                                                    |

 For more information about:  

- How the adapter supports receiving polling-based messages from Oracle database, see [Receive polling-based data-changed messages](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).  

- Receiving polling-based messages from Oracle database using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Invoke Functions and Procedures in Oracle Database using Biztalk Server](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md).  

- Receiving polling-based messages from Oracle database using WCF service model, see [Receive Polling-based Data-changed Messages from SQL Server by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md).  

- Receiving polling-based messages from Oracle database using WCF channel model, see [Receive Polling-based Data-changed Messages from SQL Server by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md).  

- Message structure and SOAP actions for performing a polling query, see [Message Schemas for the Polling Operations](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md).  

## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)