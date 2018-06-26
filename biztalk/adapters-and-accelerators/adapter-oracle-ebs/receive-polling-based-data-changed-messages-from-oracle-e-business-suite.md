---
title: "Receive polling-based data-changed messages from Oracle E-Business Suite | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbcb23d0-508d-4601-91b4-c674d76cd063
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive polling-based data-changed messages from Oracle E-Business Suite
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] supports receiving polling-based data-changed messages by polling the interface tables, interface views, tables, and views. The adapter delivers the messages to your application by:  

- Executing a SQL SELECT query to determine whether data is available for polling. You can configure the adapter to execute the SQL SELECT query periodically or continuously.  

- Executing a SQL SELECT query against an Oracle table or view or executing stored procedures, functions, or packaged procedures and functions.  

- Executing an optional post-poll PL/SQL code block on Oracle E-Business Suite. This code block is often used to update a field on the queried records in the target or to move the queried records to another table or view.  

- Returning the query results in a result set by invoking the POLL operation or the stored procedures, functions, or packaged procedures and functions that are exposed as polling operations.  

  The adapter executes all of these operations inside an Oracle transaction.  

## How Do I Configure the Oracle E-Business Adapter for Receiving Data-changed Messages Using Binding Properties?  
 You configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive data-changed messages by setting some or all of the following binding properties.  


|         Binding Property         |                                                                                                                                                                                                                                                                                                                                                                                     Value                                                                                                                                                                                                                                                                                                                                                                                     | Default |                                Required/Optional                                |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|---------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                                                                                                                                                                                                                Make sure that the value is set to **Polling**.                                                                                                                                                                                                                                                                                                                                                                | Polling |         Required. If not explicitly set, the default value will apply.          |
| **PolledDataAvailableStatement** | Specify the SELECT statement executed to determine whether any data is available for polling for a specific table. The specified statement must return a result set consisting of rows and columns. The value in the first cell of the result set indicates whether the adapter executes the value specified for the **PollingInput** binding property. If the first cell of the result contains a positive value, the adapter executes the polling statement. For example, a valid statement for this binding property will be:<br /><br /> `Select * from <table_name>`<br /><br /> **Note:** You must not specify stored procedures for this binding property. Also, this statement must not modify the data in Oracle E-Business Suite or the underlying Oracle database. |  null   |                                    Required.                                    |
|        **PollingAction**         |                                                                                                                                                                                                                                                          Specifies the action for the polling operation. You can determine the polling action for a specific operation from the metadata you generate for the operation using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].                                                                                                                                                                                                                                                          |  null   | Optional for polling operations on tables and views using the SELECT statement. |
|         **PollingInput**         |                                                                                                                                                       Specify either of the following:<br /><br /> - SQL SELECT statement that should be executed against Oracle E-Business Suite. This statement should include a FOR UPDATE clause. For information about the FOR UPDATE clause, see [Specifying a FOR UPDATE Clause in the Polling Statement](#ForUpdate) later in this topic.<br /><br /> - Request message for a stored procedure, function, or procedure or function within a package that you want to be polled.                                                                                                                                                       |  null   |     Required. Setting **PollingInput** to a non-null value enables polling.     |
|       **PollingInterval**        |                                                                                                                                                       Set to the interval, in seconds, at which you want the adapter to query Oracle E-Business Suite. This property specifies the polling interval and the polling transaction time out. The value should be greater than the amount of time it takes to execute the query and post-poll statement (if one is specified) on Oracle E-Business Suite plus the amount of time it takes for the client to process the query data and return the polling response message.                                                                                                                                                       |   30    |         Required. If not explicitly set, the default value will apply.          |
|      **PollWhileDataFound**      |                                                                                                                                                                                                      Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously polls Oracle E-Business Suite, if data is available in the table being polled. If no data is available in the table, the adapter reverts to execute the SQL statement at the specified polling interval                                                                                                                                                                                                      |  False  |         Required. If not explicitly set, the default value will apply.          |
|      **PostPollStatement**       |                                                                                                                                                                                                                                                                                                            Set to an optional PL/SQL code block that is executed by the adapter after the query is performed, but before the query data is returned to the client.                                                                                                                                                                                                                                                                                                            |  null   |   Optional. If no value is specified, a post poll statement is not executed.    |

> [!NOTE]
>  If you are using the WCF service model or the WCF channel model, you must also set the **AcceptCredentialsInUri** binding property.  

##  <a name="ForUpdate"></a> Specifying a FOR UPDATE Clause in the Polling Statement  
 If you are using a SELECT statement as the polling statement and executing a post-poll statement that affects the rows specified in the SELECT statement, you must use the FOR UPDATE clause in the polling statement. Specifying a FOR UPDATE clause ensures that the records selected by the polling statement are locked during the transaction and that the post-poll statement can perform any required updates on them.  

> [!CAUTION]
>  You can have scenarios where in the time window between the polling and post-poll statements, more records are added to the table that meet the condition of the post-poll statement. In such situations, the post-poll statement would update all the records that satisfy the condition and not just the records selected as part of the polling statement.  

 If a post-poll statement is specified and the polling statement does not contain a FOR UPDATE clause, you will experience one of the following two conditions:  

- If **TransactionIsolationLevel** is set to **ReadCommitted**, the post-poll query will not update the selected rows.  

- If **TransactionIsolationLevel** is set to **Serializable**, the following target system exception (**Microsoft.ServiceModel.Channels.Common.TargetSystemException**) will occur when the post-poll statement is executed: "ORA-08177 can't serialize access for this transaction". In such a case, you must set the **PollingRetryCount** binding property to define the number of times you want the adapter to retry the same transaction.  

  For instructions on how to set the transaction isolation level, see [Configure transaction isolation level and transaction timeout with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).  

  The polling and post-poll statements are executed in a transaction if the adapter clients have configured to use transactions and the value of the **UseAmbientTransaction** binding property is set to **True** in the adapter.  

  An example of a polling query with the FOR UPDATE option is:  

```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE  
```  

### Specifying a NOWAIT Clause in the Polling Statement  
 You may have scenarios where concurrent threads are accessing the table being polled, leading to too many contentions in the table. This may cause the polling query to be blocked to get a lock on table rows. If you are using a SELECT statement as the polling statement, you may want to specify a NOWAIT keyword along with the FOR UPDATE keyword in the SELECT statement. This will cause the polling query execution within the adapter to return immediately if there are locks on rows which the polling query is trying to select. An exception is usually thrown by Oracle under such conditions. Again, adapter clients may use the **PollingInterval** binding property to specify the time interval after which the adapter clients must retry for polling the data.  

 An example of a polling query with the NOWAIT option is:  

```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE NOWAIT  
```  

### Specifying a SKIP LOCKED Clause in the Polling Statement  
 You may have scenarios where due to concurrent threads accessing the table being polled, some rows in the result set of the WHERE clause specified in the polling query are locked. For example, your polling query returns 6 rows from a table; 4 out of these 6 rows are already locked because of some other transaction. In this case, you might want to specify a SKIP LOCKED keyword along with the FOR UPDATE keyword that instructs the database to attempt to lock the rows specified by the WHERE clause, and to skip any rows that are found to be already locked. The unlocked rows in the WHERE clause are locked during the transaction and the post-poll statement can perform any required updates on them so that these rows are not polled again. This ensures that you do not have to wait to receive the polling messages until all the rows specified by the WHERE clause are unlocked.  

 The SKIP LOCKED keyword is useful in a scenario where you have adapter clients on multiple computers that are polling the same table in a database. You can load balance among the adapter clients by configuring the polling operation in such a way that you receive polling-based data-change messages for the rows specified by the WHERE clause that are unlocked at that point of time, and then update the row to ensure that if a polling-based data-change message is received by an adapter client, the other clients do not get the same message.  

 An example of a polling query with the SKIP LOCKED option is:  

```  
SELECT * from EMP WHERE FLAG = 'Y' FOR UPDATE SKIP LOCKED  
```  

## Support for Ordered Delivery (FIFO)  
 In a production environment, polling can be used to monitor the data changes in Oracle E-Business Suite. These data-changed messages are received by the adapter client using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Based on business scenarios, it can be critical that the data-changed messages are received by the adapter client in the right order.  

 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports ordered delivery or first-in-first-out (FIFO) to maintain the order in which messages are received from Oracle E-Business Suite. Here are a few considerations related to support for FIFO in inbound scenarios for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  

- If the message is being consumed by an orchestration, the orchestration must have the ordered delivery set for the messages coming from the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] receive port.  

- If the message is being consumed by a send port (in a content-based routing) scenario, the send port must have ordered delivery set for the messages coming from the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] receive port.  

  The WCF-Custom or WCF-OracleEBS adapter has a property **Suspend request message on failure** that specifies whether to suspend the request message that fails inbound processing. This property can be set on the **Messages** tab of the WCF-Custom or WCF-OracleEBS receive port under the **Error handling** section. The following table lists the scenarios describing how the incoming messages are processed based on whether this property is set and the state of the message subscriber (orchestration or port).  

|WCF-Custom port property|Subscriber in Unenlisted state|Subscriber in Enlisted but Stopped state|  
|-------------------------------|------------------------------------|----------------------------------------------|  
|**Suspend request message on failure** property NOT set|- Routing Failure Report is generated as a suspended (non-resumable message)<br /><br /> - Actual message is not suspended<br /><br /> - Post poll query is not executed as transaction gets aborted. Hence polling repeats and fetches the rows again.<br /><br /> - Errors reported in the event log to describe what has happened.|- Not considered a “Failure”. There are no error messages in the event log.<br /><br /> - Actual message is put into the suspended (resumable) queue.<br /><br /> - When the subscribing port or orchestration starts, the messages are automatically resumed. If ordered delivery is set on the subscriber, it will be honored.<br /><br /> - The messages may also be resumed manually.|  
|**Suspend request message on failure** property IS set|- Routing Failure Report is generated as a suspended (non-resumable message)<br /><br /> - Actual message is also suspended<br /><br /> - Post poll query is not executed as transaction gets aborted. Hence polling repeats and fetches the rows again.<br /><br /> - Errors reported in the event log to describe what has happened.|- Not considered a “Failure”. There are no error messages in the event log.<br /><br /> - Actual message is put into the suspended (resumable) queue.<br /><br /> - When the subscribing port or orchestration starts, the messages are automatically resumed. If ordered delivery is set on the subscriber, it will be honored.<br /><br /> - The messages may also be resumed manually.|  

## See Also  
 [Development Activities](../../esb-toolkit/development-activities.md)   
 [Poll Oracle E-Business Suite Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)