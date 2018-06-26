---
title: "Poll Oracle Database using the SELECT statement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "polling-based notifications, receiving from Oracle"
  - "polling query, configuring a"
ms.assetid: d2689eb9-6f17-498f-8a32-07f43a368833
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Poll Oracle Database using the SELECT statement
You can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive periodic data-change messages by using a SELECT statement to continuously poll the tables and views in Oracle the Oracle database. You can specify a SELECT statement as a polling statement that the adapter executes periodically to poll the Oracle database. Optionally, you can also specify a post-poll PL/SQL code block that the adapter executes if there is a change in data. This block is often used to update a field on the queried records in the target or to move the queried records to another table or view.  

 To enable this, you must specify certain binding properties on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. You can also modify the target namespace for the POLLINGSTMT operation by setting the **PollingId** property in the connection URI. For more information, see [Support for Receiving Polling-based Data-changed Messages in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md) and [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md). For information about the structure of the SOAP message for polling operations, see [Message Schemas for the Polling Operations2](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md).  

## Configuring a Polling Operation with Oracle Database Adapter Binding Properties  
 The following table summarizes the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties that you use to configure the adapter to receive data change messages. You must specify these binding properties while configuring the receive port in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  


|         Binding Property         |                                                                                                                                                                                                                      Description                                                                                                                                                                                                                      |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                       Specifies whether you want to perform Polling or Notification inbound operation. Default is **Polling**.                                                                                                                                                                        |
| **PolledDataAvailableStatement** |                        Specifies the SQL statement that the adapter executes to determine whether any data is available for polling. Only if a record is available, the SELECT statement you specify for the **PollingStatement** binding property will be executed. The default is `SELECT 1 FROM DUAL`, which implies that the adapter must continue polling irrespective of whether the table being polled has data or not.                        |
|       **PollingInterval**        | Specifies the interval, in seconds, at which the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property. The default is 500 seconds. The polling interval determines the time interval between successive polls. If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval. |
|       **PollingStatement**       |                 Specifies the polling statement. To poll using a SELECT statement, you must specify a SELECT statement for this binding property. The default is null.<br /><br /> You must specify a value for **PollingStatement** binding property to enable polling. The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.                 |
|        **PollingAction**         |                                                                                              Specifies the action for the polling operation. You can determine the polling action for a specific operation from the metadata you generate for the operation using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].                                                                                              |
|      **PostPollStatement**       |                                                                                                                                                         Specifies a statement block that is executed after the statement specified by the **PollingStatement** binding property is executed.                                                                                                                                                          |
|      **PollWhileDataFound**      |                                     Specifies whether the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled. If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval. Default is false.                                     |

 For a more complete description of these properties, see [Read about the   Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). For a complete description of how to use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to poll the Oracle database, read further.  

## How This Topic Demonstrates Polling  
 In this topic, to demonstrate how the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports receiving data change messages using SELECT statements, create a BizTalk project and generate schema for the **POLLINGSTMT** operation by setting the **PollingStatement** binding property to the following:  

```  
SELECT * FROM ACCOUNTACTIVITY FOR UPDATE  
```  

 The ACCOUNTACTIVITY table is created when you run the SQL scripts provided with the samples to create these objects in the database.  

> [!NOTE]
>  The orchestration in this topic polls the ACCOUNTACTIVITY table, which is a base database table created by running the scripts provided with the samples. You must perform similar procedures as described in this topic to poll any other table.  

 To demonstrate a polling operation, we do the following:  

-   Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the table being polled (ACCOUNTACTIVITY) has any data. In this example, you can set this binding property as:  

    ```  
    SELECT COUNT (*) FROM ACCOUNTACTIVITY  
    ```  

     This ensures that the adapter executes the polling statement only when the ACCOUNTACTIVITY table has some records.  

-   Specify the SELECT statement as stated earlier for the **PollingStatement** binding property. This statement retrieves all the rows in the ACCOUNTACTIVITY table.  

-   EXECUTE a PL/SQL block as part of the **PostPollStatement** binding property. This statement will move all data from ACCOUNTACTIVITY table to another table in the database. Once this happens, the next time the statement specified for **PollingStatement** will be executed, it will not fetch any data.  

-   Until more data is added to the ACCOUNTACTIVITY table, you will not get any polling messages. So, you must repopulate the ACCOUNTACTIVITY table with new records. You can do so by running the more_activity_data.sql script provided with the samples. After you run this script, the next polling operation will fetch the new records inserted into the table.  

## How to Receive Data-change Messages from Oracle  
 Performing an operation on Oracle database using [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves the following procedural tasks described in [Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md). To configure the adapter to poll Oracle database using a SELECT statement, these tasks are:  

1. Create a BizTalk project, and generate schema for the **POLLINGSTMT** operation for the table you want to poll.  

2. Create a message in the BizTalk project for receiving messages from Oracle database.  

3. Create an orchestration to receive messages from Oracle and save them to a folder.  

4. Build and deploy the BizTalk project.  

5. Configure the BizTalk application by creating physical send and receive ports.  

   > [!IMPORTANT]
   >  For inbound polling scenarios you must always configure a one-way receive port. Two-way receive ports are not supported for inbound operations.  

6. Start the BizTalk application.  

   This topic provides instructions to perform these tasks.  

## Generating Schema  
 You must generate the schema for the **POLLINGSTMT** operation. Perform the following tasks while generating the schema using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  

- Specify a value for **PollingStatement** binding property while generating the schema. For more information about this binding property, see [Read about the   Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). For example, specify the following as a polling statement:  

  ```  
  SELECT * FROM ACCOUNTACTIVITY FOR UPDATE  
  ```  

- Select the contract type as **Service (Inbound operation)**.  

- Generate schema for the **POLLINGSTMT** operation.  

  For more information about how to generate schema, see [Browse, search, and get metadata for Oracle Database operations](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md).  

## Defining Messages and Message Types  
 The schema that you generated earlier describes the "types" required for the messages in the orchestration. A message is typically a variable, the type for which is defined by the corresponding schema. Once the schema is generated, you must link it to the messages from the Orchestration view of the BizTalk project.  

 For this topic, you must create one message to receive messages from Oracle.  

 Perform the following steps to create messages and link them to schema.  

#### To create messages and link to schema  

1.  Add an orchestration to the BizTalk project. From the Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**. Type a name for the BizTalk orchestration and then click **Add**.  

2.  Open the orchestration view window of the BizTalk project, if it is not already open. Click **View**, point to **Other Windows**, and then click **Orchestration View**.  

3.  In the **Orchestration View**, right-click **Messages**, and then click **New Message**.  

4.  Right-click the newly created message, and then select **Properties Window**.  

5.  In the **Properties** pane for **Message_1**, do the following:  

    |Use this|To do this|  
    |--------------|----------------|  
    |Identifier|Type **Receive**.|  
    |Message Type|From the drop-down list, expand **Schemas**, and select *TablePolling.OracleDBBinding*, where *TablePolling* is the name of your BizTalk project. *OracleDBBindingSchema* is the response schema generated for the **POLLINGSTMT** operation on ACCOUNTACTIVITY table.<br /><br /> **Important** Because polling is a one way operation, the schema generated by the adapter does not contain a response node, and hence there is only one root node in the schema. If you use such schemas for a message type, you must identify the schema by the filename of the generated schema.<br /><br /> For example, if you create schema for a two-way operation, the nodes in the schema file with a name `OracleDBBindingSchema` may look like “Request” and “Response”. If you want to create a message in the orchestration that maps to the request schema, you can identify the schema in the list by looking for `OracleDBBindingSchema.Request`. However, in the case of polling operation, because the only node is “POLLINGSTMT”, it is not easy to identify the schema you want to map to because schemas with single nodes are not listed as \<schemafilename\>.\<rootnodename\>. Instead, such schemas are listed by only the filename. In such a case, the only way to identify the schema is by the schema filename, for example, OracleDBBindingSchema.|  

## Setting up the Orchestration  
 You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for receiving polling-based data-change messages from Oracle. In this orchestration, the adapter receives the response by executing the SELECT statement specified for the **PollingStatement** binding property. The response message for the SELECT statement is saved to a FILE location. A typical orchestration for polling Oracle database would contain:  

- Receive and Send shapes to receive messages from Oracle and send to a FILE port, respectively.  

- A one-way receive port to receive messages from Oracle database.  

  > [!IMPORTANT]
  >  For inbound polling scenarios you must always configure a one-way receive port. Two-way receive ports are not supported for inbound operations.  

- A one-way send port to send polling responses from Oracle database.  

  A sample orchestration resembles the following.  

  ![Orchestration for a polling query for Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/6eddfe32-bfd0-4bd9-9e2a-fb4a7d0b53e3.gif "6eddfe32-bfd0-4bd9-9e2a-fb4a7d0b53e3")  

### Adding Message Shapes  
 Make sure you specify the following properties for each of the message shapes. The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.  

|Shape|Shape Type|Properties|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|- Set **Name** to *ReceiveMessage*<br /><br /> - Set **Activate** to *True*|  
|SaveMessage|Send|- Set **Name** to *SaveMessage*|  

### Adding Ports  
 Make sure you specify the following properties for each of the logical ports. The names listed in the Port column are the names of the ports as displayed in the orchestration.  

|Port|Properties|  
|----------|----------------|  
|OracleReceivePort|- Set **Identifier** to *OracleReceivePort*<br /><br /> - Set **Type** to *OracleReceivePortType*<br /><br /> - Set **Communication Pattern** to *One-Way*<br /><br /> - Set **Communication Direction** to *Receive*|  
|SaveMessagePort|- Set **Identifier** to *SaveMessagePort*<br /><br /> - Set **Type** to *SaveMessagePortType*<br /><br /> - Set **Communication Pattern** to *One-Way*<br /><br /> - Set **Communication Direction** to *Send*|  

### Specify Messages for Action Shapes and Connect to Ports  
 The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports. The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.  

|Shape|Properties|  
|-----------|----------------|  
|ReceiveMessage|- Set **Message** to *Receive*<br /><br /> - Set **Operation** to *OracleReceivePort.Polling.Request*|  
|SaveMessage|- Set **Message** to *Receive*<br /><br /> - Set **Operation** to *SaveMessagePort.Polling.Request*|  

 After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.  

 You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).  

## Configuring the BizTalk Application  
 After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the BizTalk Server Administration console. You must use the BizTalk Server Administration console to configure the application. For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).

 Configuring an application involves:  

- Selecting a host for the application.  

- Mapping the ports that you created in your orchestration to physical ports in the BizTalk Server Administration console. For this orchestration you must:  

  - Define a location on the hard disk and a corresponding FILE port where the BizTalk orchestration will drop the messages from Oracle. These messages will be in response to the polling statement that you specify for the receive port.  

  - Define a physical WCF-Custom or WCF-OracleDB one-way receive port. This port polls the Oracle database. For information about how to create receive ports, see [Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md). Make sure you specify the following binding properties for the receive port.  

    |Binding Property|Value|  
    |----------------------|-----------|  
    |**InboundOperationType**|Set this to **Polling**.|  
    |**PolledDataAvailableStatement**|For this example, set this binding property to:<br /><br /> `SELECT COUNT (*) FROM ACCOUNTACTIVITY`<br /><br /> This ensures that the adapter executes the polling statement only when the ACCOUNTACTIVITY table has some records.|  
    |**PollingStatement**|For this binding property, specify a SELECT statement to retrieve all records from ACCOUNTACTIVITY table. For this example, set this binding property to:<br /><br /> `SELECT * FROM ACCOUNTACTIVITY FOR UPDATE`|  
    |**PostPollStatement**|Specify the post-poll statement to move all data from ACCOUNTACTIVITY table to another table. For this example, set this binding property to:<br /><br /> `BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;`|  

     For more information about the different binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  

    > [!NOTE]
    >  We recommend configuring the transaction isolation level and the transaction timeout while performing inbound operations using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. You can do so by adding the service behavior while configuring the receive port. For instruction on how to add the service behavior, see [Configure transaction isolation level and transaction timeout](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md).  

## Starting the Application  
 You must start the BizTalk application for polling Oracle database. For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).  

 At this stage, make sure:  

-   The WCF-Custom or WCF-OracleDB one-way receive port, which polls Oracle using the SELECT statement specified for the **PollingStatement** binding property, is running.  

-   The FILE send port, which receives messages from Oracle database, is running.  

-   The BizTalk orchestration for the operation is running.  

## Executing the Operation  
 After you run the application, the following set of actions take place, in the same sequence:  

-   The adapter executes the **PolledDataAvailableStatement** which returns a positive value indicating the adapter to execute the statement specified for **PollingStatement** binding property.  

-   The adapter executes the SELECT statement for the **PollingStatement** binding property and returns all the rows in the ACCOUNTACTIVITY table. The response from Oracle database resembles the following:  

    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <POLLINGSTMT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT">  
      <POLLINGSTMTRECORD>  
        <POLLINGSTMTRECORD>  
          <TID>1</TID>   
          <ACCOUNT>100001</ACCOUNT>   
          <AMOUNT>500</AMOUNT>   
          <DESCRIPTION />   
          <TRANSDATE>2008-08-03T20:10:28</TRANSDATE>   
          <PROCESSED>n</PROCESSED>   
        <POLLINGSTMTRECORD>  
      <POLLINGSTMTRECORD>  
          ......  
          ......  
      </POLLINGSTMTRECORD>  
        ......  
        ......  
      </POLLINGSTMTRECORD>  
    </POLLINGSTMT>  
    ```  

-   The adapter executes the post-poll statement, which moves all the data from ACCOUNTACTIVITY table to another table.  

-   After the polling interval, the adapter again executes **PolledDataAvailableStatement**. Because ACCOUNTACTIVITY table has no records now, **PolledDataAvailableStatement** does not return a positive value and hence the adapter does not execute the statement specified for the **PollingStatement** binding property. As a result, adapter client does not get any polling message.  

-   The adapter client will not get any more polling messages until some records are explicitly inserted into the ACCOUNTACTIVITY table. To insert more records, you can run the more_activity_data.sql script provided with the samples. After you run this script, the next time **PolledDataAvailableStatement** is executed, it returns a positive value. As a result, the adapter executes the polling statement and adapter clients again receive a polling message.  

> [!NOTE]
>  The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] will continue to poll until you explicitly disable the receive port from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

## Possible Exceptions  
 For information about the exceptions you might encounter while running a polling query on the Oracle database using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Exceptions and error handling with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md).  

## Best Practices  
 After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the bindings file. Once you generate a bindings file, you can import the configuration settings from the file so that you do not need to create the send ports and receive ports for the same orchestration. For more information about binding files, see [Reuse Oracle Database Adapter bindings](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).  

## See Also  
 [Poll Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-biztalk-server.md)