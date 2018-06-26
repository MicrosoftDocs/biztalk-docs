---
title: "Receive polling messages using SELECT statements with FOR XML Clause from SQL using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65c629c1-9ef7-4aa1-8ec1-f94a3cb41cb0
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive polling messages using SELECT statements with FOR XML Clause from SQL using BizTalk Server
You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive periodic data-change messages for SQL Server tables or views by using SELECT statements or stored procedures that include a FOR XML clause. You can specify these statements as polling statement that the adapter executes to poll the database. The polling statement can be a SELECT statement or a stored procedure that returns a result set.  
  
 For more information on how the adapter supports polling, see [Support for Polling](https://msdn.microsoft.com/library/dd788416.aspx). For information about the structure of the SOAP message for polling operations, see [Message Schemas for the Polling and TypedPolling Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md). The SQL [FOR XML clause](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server) provides more details.
  
> [!NOTE]
>  This topic demonstrates how to use the **XmlPolling** inbound operation to receive polling messages. The **XmlPolling** operation is used to poll a SQL Server database using SELECT statements or stored procedures that include a FOR XML clause. The message for the **XmlPolling** operation includes the xml message received by executing the SELECT statement or the stored procedure in SQL Server Management Studio.  
> 
>  You can also use the adapter to receive different types of polling messages.  
> 
> - If you want to get a weakly-typed polling message, you must use the Polling Operation. For more information, see [Receive Polling-based Data-changed Messages from SQL Server by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md).  
>   -   If you want to get strongly-typed polling message, you must use the **TypedPolling** operation. You must also use the **TypedPolling** operation to have multiple polling operations in a single BizTalk application. For instructions on how to perform **TypedPolling** operation, see [Receive Strongly-typed Polling-based Data-changed Messages from SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md).  
> 
> [!IMPORTANT]
>  If you want to have more than one polling operation in a single BizTalk application, you must specify an **InboundID** connection property as part of the connection URI to make it unique. With a unique connection URI, you can create multiple receive ports that poll the same database, or even the same table in a database. For more information, see [Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md).  
  
## How This Topic Demonstrates Polling  
 In this topic, to demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving data change messages, we use a SELECT statement with the FOR XML clause to poll the SQL Server database. When you invoke such a statement in SQL Server Management Studio, the output is in the form of an xml message. To use such statements to poll a SQL Server database, you must have the schema of the response xml message. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] requires this schema to receive a polling message after executing a SELECT statement with the FOR XML clause. So, to use a SELECT statement with FOR XML clause to poll the SQL Server database, you must perform the following set of tasks.  
  
1.  Generate the schema for the XML response message for the SELECT statement with FOR XML clause.  
  
2.  Create a BizTalk project and add the generated schema to the project.  
  
3.  Create a message in the BizTalk project for receiving XML response messages from the SQL Server database.  
  
4.  Create an orchestration to receive messages from the SQL Server database and to save them to a folder.  
  
5.  Build and deploy the BizTalk project.  
  
6.  Configure the BizTalk application by creating physical send and receive ports.  
  
    > [!IMPORTANT]
    >  For inbound polling scenarios you must always configure a one-way WCF-Custom or WCF-SQL receive port. Two-way WCF-Custom or WCF-SQL receive ports are not supported for inbound operations.  
  
7.  Start the BizTalk application.  
  
##  <a name="BKMK_RespSchema"></a> Generating Schema for the Response Message for SELECT Statement  
 You can generate the schema for the response message for the SELECT statement by including the `xmlschema` clause with the `for xml` clause. In this topic, we use a SELECT statement to retrieve employee details for a given employee ID. To retrieve the schema by executing a SELECT statement, the SELECT statement must be written in the following manner:  
  
```  
SELECT Employee_ID ,Name ,Designation FROM Employee for xml auto, xmlschema  
```  
  
 Execute this SELECT statement to get the schema for the response message. Save the schema. You must now create a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and add this schema to the project. For this example, you can name this schema as **PollingResponse.xsd**.  
  
> [!IMPORTANT]
>  Make sure you remove the `xmlschema` clause after you have executed the SELECT statement to generate the schema. If you fail to do this, when you finally execute the SELECT statement through BizTalk as part of the XmlPolling operation, you will again generate the schema in the response message. So, to get the response message as xml you must remove the `xmlschema` clause.  
  
#### To add the schema to a BizTalk project  
  
1. Create a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
2. Add the response schema you generated for the stored procedure to the BizTalk project. Right-click the BizTalk project in the Solution Explorer, point to **Add**, and then click **Existing Item**. In the Add Existing Item dialog box, navigate to the location where you saved the schema and click **Add**.  
  
3. Open the schema in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and make the following changes.  
  
   1.  Add a node to the schema and move the existing root node under this newly added node. Give a name to the root node. For this topic, rename the root node to **Root**.  
  
   2.  The response schema generated for the SELECT statement references a sqltypes.xsd. You can get the sqltypes.xsd schema from [http://go.microsoft.com/fwlink/p/?LinkId=131087](http://go.microsoft.com/fwlink/p/?LinkId=131087). Add the sqltypes.xsd schema to the BizTalk project.  
  
   3.  In the schema generated for the SELECT statement, change the value of `import schemaLocation` to the following.  
  
       ```  
       import schemaLocation=”sqltypes.xsd”  
       ```  
  
        You do this because you have already added the sqltypes.xsd schema to your BizTalk project.  
  
   4.  Provide a target namespace for the schema. Click the **\<Schema\>** node, and in the properties pane, specify a namespace in the **Target Namespace** property. For this topic, give the namespace as `http://ForXmlPolling/namespace`.  
  
## Defining Messages and Message Types  
 The schema that you generated earlier describes the "types" required for the messages in the orchestration. A message is typically a variable, the type for which is defined by the corresponding schema. Once the schema is generated, you must link it to the messages from the Orchestration view of the BizTalk project.  
  
 For this topic, you must create one message to receive messages from the SQL Server database.  
  
 Perform the following steps to create messages and link them to schema.  
  
#### To create messages and link to schema  
  
1.  Add an orchestration to the BizTalk project. From the Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**. Type a name for the BizTalk orchestration and then click **Add**.  
  
2.  Open the orchestration view window of the BizTalk project, if it is not already open. Click **View**, point to **Other Windows**, and then click **Orchestration View**.  
  
3.  In the **Orchestration View**, right-click **Messages**, and then click **New Message**.  
  
4.  Right-click the newly created message, and then select **Properties Window**.  
  
5.  In the **Properties** pane for **Message_1**, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |Identifier|Type **PollingMessage**.|  
    |Message Type|From the drop-down list, expand **Schemas**, and select *ForXMLPolling.PollingResponse*, where *ForXMLPolling* is the name of your BizTalk project. *PollingResponse* is the name of the response schema generated by executing the SELECT statement as described under [Receive polling messages using SELECT statements with FOR XML Clause from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md).|  
  
## Setting up the Orchestration  
 You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for receiving polling-based data-change messages from the SQL Server database. In this orchestration, the adapter receives the response of the select statement specified for the **PollingStatement** binding property. The response for the SELECT statement is saved to a FILE location. A typical orchestration for polling a SQL Server database would contain:  
  
- Receive and Send shapes to receive messages from SQL Server and send to a FILE port, respectively.  
  
- A one-way receive port to receive messages from SQL Server.  
  
  > [!IMPORTANT]
  >  For inbound polling scenarios you must always configure a one-way receive port. Two-way receive ports are not supported for inbound operations.  
  
- A one-way send port to send polling responses from a SQL Server database to a folder.  
  
  A sample orchestration resembles the following.  
  
  ![Orchestration for polling a SQL Server database](../../adapters-and-accelerators/adapter-sql/media/5cf65d53-d70d-444d-82f7-2561efcd9ee4.gif "5cf65d53-d70d-444d-82f7-2561efcd9ee4")  
  
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
|SQLReceivePort|- Set **Identifier** to *SQLReceivePort*<br /><br /> - Set **Type** to *SQLReceivePortType*<br /><br /> - Set **Communication Pattern** to *One-Way*<br /><br /> - Set **Communication Direction** to *Receive*|  
|SaveMessagePort|- Set **Identifier** to *SaveMessagePort*<br /><br /> - Set **Type** to *SaveMessagePortType*<br /><br /> - Set **Communication Pattern** to *One-Way*<br /><br /> - Set **Communication Direction** to *Send*|  
  
### Specify Messages for Action Shapes and Connect to Ports  
 The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports. The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.  
  
|Shape|Properties|  
|-----------|----------------|  
|ReceiveMessage|- Set **Message** to *Receive*<br /><br /> - Set **Operation** to *SQLReceivePort.XmlPolling.Request*|  
|SaveMessage|- Set **Message** to *Receive*<br /><br /> - Set **Operation** to *SaveMessagePort.XmlPolling.Request*|  
  
 After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.  
  
 You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).
  
## Configuring the BizTalk Application  
 After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the BizTalk Server Administration console. You must use the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the application. For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuring an application involves:  
  
- Selecting a host for the application.  
  
- Mapping the ports that you created in your orchestration to physical ports in the BizTalk Server Administration console. For this orchestration you must:  
  
  - Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the messages from the SQL Server database. These messages will be in response to the polling statement that you specify for the receive port.  
  
  - Define a physical WCF-Custom or WCF-SQL one-way receive port. This port polls the SQL Server database with the polling statement you specify for the port. For information about how to create ports, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md). Make sure you specify the following binding properties for the receive port.  
  
    > [!IMPORTANT]
    >  You do not need to perform this step if you specified the binding properties at design-time. In such a case, you can create a WCF-custom or WCF-SQL receive port, with the required binding properties set, by importing the binding file created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. For more information see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).  
  
    |Binding Property|Value|  
    |----------------------|-----------|  
    |**InboundOperationType**|Make sure you set this to **XmlPolling**.|  
    |**PolledDataAvailableStatement**|Make sure you specify a SQL statement. For this topic, specify:<br /><br /> `SELECT COUNT(*) FROM Employee`|  
    |**PollingStatement**|Make sure you provide the same statement, without the `xmlschema` clause, that you specified while generating the schema as described in [Receive polling messages using SELECT statements with FOR XML Clause from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md).<br /><br /> `SELECT Employee_ID ,Name ,Designation FROM Employee for xml auto`<br /><br /> **Note:** Note that the SELECT statement does not contain the `xmlschema` clause.|  
    |**XmlStoredProcedureRootNodeName**|Specify the name of the root node that you added to the response schema you generated for the SELECT statement, as described under [Generating Schema for the Response Message for SELECT Statement](#BKMK_RespSchema). For this topic, set this to **Root**.|  
    |**XmlStoredProcedureRootNodeNamespace**|Specify the target namespace for the response schema you generated for the SELECT statement, as described under [Generating Schema for the Response Message for SELECT Statement](#BKMK_RespSchema). For this topic, set this to `http://ForXmlPolling/namespace`.|  
  
     For more information about the different binding properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
    > [!NOTE]
    >  We recommend configuring the transaction isolation level and the transaction timeout while performing inbound operations using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. You can do so by adding the service behavior while configuring the WCF-Custom or WCF-SQL receive port. For instruction on how to add the service behavior, see [Configure Transaction Isolation Level and Transaction Timeout with SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).  
  
## Starting the Application  
 You must start the BizTalk application for receiving messages from the SQL Server database. For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).
  
 At this stage, make sure:  
  
-   The WCF-Custom or WCF-SQL one-way receive port, which polls the SQL Server database using the statements specified for the **PollingStatement** binding property, is running.  
  
-   The FILE send port, which receives messages from SQL Server, is running.  
  
-   The BizTalk orchestration for the operation is running.  
  
## Executing the Operation  
 After you run the application, the following set of actions take place, in the same sequence:  
  
-   The adapter executes the **PolledDataAvailableStatement** on the Employee table and determines that the table has records for polling.  
  
-   The adapter executes the polling statement and receives a polling message from the SQL Server database. Because the polling statement consists of a SELECT statement with a FOR XML clause, the polling message received by the adapter resembles the following:  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Root xmlns="http://ForXmlPolling/namespace">  
      <Employee Employee_ID="10765" Name="John" Designation="Tester" xmlns="" />   
      <Employee Employee_ID="10766" Name="Sam" Designation="Manager" xmlns="" />   
      .....  
      .....  
    </Root>  
    ```  
  
     Notice that the polling message is received in the same schema as generated by executing the SELECT statement with the **xmlschema** clause. Also note that the root node and the namespace is the same you specified as values for **XmlStoredProcedureRootNodeName** and **XmlStoredProcedureRootNodeNamespace** binding properties respectively.  
  
> [!NOTE]
>  The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] will continue to poll until you explicitly disable the receive port from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
## Best Practices  
 After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file. Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create the send ports and receive ports for the same orchestration. For more information about binding files, see [Reuse adapter bindings](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## See Also  
 [Poll SQL Server by Using the SQL Adapter with BizTalk Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)