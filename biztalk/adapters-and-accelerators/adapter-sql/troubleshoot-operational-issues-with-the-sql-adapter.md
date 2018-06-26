---
title: "Troubleshoot Operational Issues with the SQL adapter in BizTalk| Microsoft Docs"
description: Common issues and resolutions for the SQL adapter in the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c75f85f4-cd03-4c6a-aac9-a6d02d3c3449
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot Operational Issues with the SQL adapter
This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].  
  
## Enabling Tracing  
 You must enable tracing between the adapter, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], and SQL Server to gather more information about any issues you encounter while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. For more information about tracing support in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Diagnostic Tracing and Message Logging in the SQL adapter](../../adapters-and-accelerators/adapter-sql/diagnostic-tracing-and-message-logging-in-the-sql-adapter.md).  
  
## Known Issues  
 The following are the most common errors you might encounter when using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], along with their probable cause and resolution.  
  
  
  
###  <a name="BKMK_SQLLoadBinding"></a> Error in loading the adapter bindings  
 **Problem**  
  
 When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you get the following error:  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **Cause**  
  
 When you try to start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters. In turn, the adapter bindings are dependent on the specific client software for the enterprise application. You might face this issue if you did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. However, the LOB client libraries might be installed for only one enterprise application. As a result, the GUI fails to load the bindings for the other adapters.  
  
 **Resolution**  
  
 Make sure you do a custom installation of the adapters to install only the adapter you need.  
  
###  <a name="BKMK_SQLDisplay"></a> The SQL adapter does not display in the list of adapters in BizTalk Server Administration console  
 **Problem**  
  
 Unlike the earlier version of the adapters shipped with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
 **Cause**  
  
 The latest [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding. So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 **Resolution**  
  
 You can explicitly add the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).  
  
###  <a name="BKMK_MissingAction"></a> Error while performing operations on a SQL Server database  
 **Problem**  
  
 The adapter gives the following error when performing any operation on a SQL Server database using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
- **For BizTalk Server**  
  
  ```  
  System.ArgumentNullException: Value cannot be null.  
  ```  
  
  **Cause**  
  
  The WCF action for the message is not specified. WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.  
  
  **Resolution**  
  
  Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration. For instructions, see [Configure the SOAP action for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md). See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md) to see a list of actions for each operation.  
  
###  <a name="BKMK_SQLInvalidOp"></a> InvalidOperationException with ErrorCode=5 while performing FILESTREAM operations  
 **Problem**  
  
 You get the following error while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform FILESTREAM operations.  
  
```  
System.InvalidOperationException: OpenSqlFileStream returned error.  
ErrorCode:5  
  
```  
  
 **Cause**  
  
 You might have specified database credentials to connect to the SQL Server database. To perform FILESTREAM operations, you must always use Windows Authentication. The error code “5” denotes that access is denied because of incorrect credentials. For more information about the different error codes, see [System Error Codes (0-499)](https://msdn.microsoft.com/library/ms681382(VS.85).aspx).
  
 **Resolution**  
  
 Use Windows Authentication to connect to the SQL Server database. In [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can do so by leaving the user name and password fields blank in the WCF-Custom or WCF-SQL port configuration dialog box.  
  
###  <a name="BKMK_SQLPolling"></a> Polling operation does not return any messages even if valid statements are specified for PollingStatement and PolledDataAvailableStatement  
 **Problem**  
  
 Even if valid values are specified for the PollingStatement and PolledDataAvailableStatement binding properties, the adapter does not receive a polling message from SQL Server.  
  
 **Cause**  
  
 Verify whether any other transaction has taken a lock on the table that the adapter is polling.  
  
 **Resolution**  
  
 If you want to poll a table that is being updated as part of another transaction, you can consider using “with (nolock)” parameter as part of the query specified for PolledDataAvailableStatement binding property to ensure that data is returned even if a lock is imposed by the other transaction. For more information, see [SQL Locking in the Database Engine](https://msdn.microsoft.com/library/ms190615.aspx).
  
###  <a name="BKMK_SQLSingleOp"></a> The adapter fails to insert, update, or delete large volumes of data in a single operation using BizTalk Server  
 **Problem**  
  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] fails to insert, update, or delete large volumes of data in a single operation using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 **Cause**  
  
 Inserting, updating, or deleting large volumes of data may take time and the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] or the transaction in which the operation is being performed, may time out.  
  
 **Resolution**  
  
- **For BizTalk Server**  
  
  1. Specify the timeout for the WCF adapter in the machine.config. Navigate to the machine.config file under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG and add the excerpt that resembles the following.  
  
     ```  
     <configuration>  
      <system.transactions>  
       <machineSettings maxTimeout="02:00:00" />  
      </system.transactions>  
     </configuration>  
     ```  
  
      With this setting, the WCF adapter timeout is set to 2 hours.  
  
  2. Specify the timeout settings for MSDTC transactions in the machine.config. Navigate to the machine.config file under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG and add the excerpt that resembles the following.  
  
     ```  
     <system.transactions>   
             <defaultSettings distributedTransactionManagerName="<computer_name>" timeout="02:00:00"/>   
         </system.transactions>  
  
     ```  
  
      With this setting, the MSDTC timeout is set to 2 hours. The default value for MSDTC timeout is 10 minutes.  
  
     > [!IMPORTANT]
     >  You must make this change on the computers running the adapter client and SQL Server. In the excerpt, replace <computer_name> with the name of computer running the adapter client and SQL Server.  
  
  3. Set the **SendTimeout** binding property for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to a fairly large value. For instructions on how to set the binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
###  <a name="BKMK_SQLFullSchemaValidate"></a> Full schema validation in BizTalk Server fails for response messages containing DataSet  
 **Problem**  
  
 For operations that return a response message containing a DataSet, for example ExecuteReader, full schema validation fails in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 **Resolution**  
  
 We recommend you to not do a full schema validation for response messages containing a dataset. Instead, you could do the following:  
  
1.  Execute the operation once that returns the response message with the schema.  
  
2.  Copy the schema from the response message to a .xsd file and add this file to your BizTalk project.  
  
3.  Use an xpath query in your orchestration to extract the data from the response message.  
  
###  <a name="BKMK_SQLRootNode"></a> Error with RootNode TypeName in BizTalk Projects  
 **Problem**  
  
 In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **Resolution**  
  
1.  Right-click the rood node referenced in the error and select **Properties**.  
  
2.  For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).  
  
###  <a name="BKMK_SQLMetadataStronglyTyped"></a> Adapter fails to generate metadata of strongly-typed stored procedure with temporary tables  
 **Problem**  
  
 The adapter fails to generate metadata for strongly-typed stored procedures that include temporary tables in their definition. The adapter gives the following exception.  
  
```  
Microsoft.ServiceModel.Channels.Common.MetadataException:  
Retrieval of Operation Metadata has failed while building WSDL at 'TypedProcedure/<schema>/<stored_procedure_name>' --->  
System.Data.SqlClient.SqlException: Invalid object name '<temp_table_name>'.  
  
```  
  
 **Resolution**  
  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support generating metadata for strongly-typed stored procedures that contain temporary tables in their definition. Instead, you should generate metadata for the same procedure from under the **Procedures** node while using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
###  <a name="BKMK_SQLVS2008"></a> Invalid binding warning when using the adapter in Visual Studio  
 **Problem**  
  
 When you use the adapter to create an application in Visual Studio and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:  
  
```  
The element 'bindings' has invalid child element 'sqlBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **Cause**  
  
 This warning appears because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding, `sqlBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].  
  
 **Resolution**  
  
 You can safely ignore this warning.  
  
###  <a name="BKMK_SQLNotification"></a> BizTalk Server throws an exception if you use more than one Notification schema in the same application or use the Notification schema across multiple applications on the same host  
 **Problem**  
  
 BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.  
  
 **Cause**  
  
 This happens because of either of the following:  
  
- You have generated more than one Notification schema in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to receive notifications from the SQL Server database. Because the Notification schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.  
  
- In case of multiple projects, you have generated a Notification schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to receive notifications from the SQL Server database. Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.  
  
  **Resolution**  
  
  Use a single Notification schema file for a BizTalk Server application. If you need to use the Notification schema in multiple BizTalk Server applications on the same host, create an application containing a single Notification schema, and then use the notification schema from all other applications in BizTalk Server.  
  
###  <a name="BKMK_SQLRestoreConn"></a> Adapter client throws an exception on performing an operation after the connectivity is restored between the adapter client and the SQL Server database  
 **Problem**  
  
 Adapter client throws the following exception on executing an operation on the SQL Server database:  
  
```  
{System.Data.Common.DbException} = {"A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.)"}  
```  
  
 **Cause**  
  
 During the execution of an operation, the adapter uses the connection from the SQL ADO.NET connection pool to connect to the SQL Server database, and perform the operation. If there is a brief network outage between the adapter client and the SQL Server database or if the SQL Server database is down temporarily, all the connections in the SQL ADO.NET connection pool become invalid. After the connectivity is restored and you try to perform an operation on the SQL Server database, the adapter uses the same invalid connections from the SQL ADO.NET connection pool, and therefore the adapter client throws the exception.  
  
 **Resolution**  
  
 The adapter client should implement retry logic in their operation execution where they should catch the exception and specify the operation retry count as “n+1”, where “n” is the value specified for the MaxConnectionPoolSize binding property. This implies that if there are “n” number of connections in the connection pool that have been rendered invalid, theoretically the adapter client should retry for a maximum of “n+1” times to get a valid connection, and hence perform the operation.  
  
 For example, to specify the retry count in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], open the **Properties** dialog box of a send port in an application, click **Transport Advanced Options** in the left pane of the dialog box, and in the **Transport Options** area, specify a value in the **Retry count** list.  
  
###  <a name="BKMK_MemUsage"></a> Memory usage and thread count increases when using the adapter in a transacted inbound operation  
 **Problem**  
  
 In a transacted inbound operation, such as Polling, **if there is no data available in the table being polled** and the adapter continues to poll, over a period of time you experience an increase in the memory usage and the thread count.  
  
 **Cause**  
  
 **If there is no data available in the table being polled**, after every receive timeout cycle, [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] spawns a new thread to continue the polling operation. Hence, the thread count and memory usage increases over a period of time. However, if the table being polled has some data, the same thread continues to perform all subsequent polls.  
  
 **Resolution**  
  
 We recommend setting the **ReceiveTimeout** to the maximum possible value, which is 24.20:31:23.6470000 (24 days) so that a new thread is spawned only every 24 days. This will ensure that the memory usage and thread count does not grow too much too soon.  
  
> [!NOTE]
>  If SqlAdapterInboundTransactionBehavior has been set, make sure the TransactionTimeout is also configured to maximum possible value, which is 24.20:31:23.6470000 (24 days). When using this workaround, we can add the SqlAdapterInboundTransactionBehavior only if the transaction isolation level has to be configured. Else, it is a best practice to remove that behavior.  
  
 For more information about the **ReceiveTimeout** binding property, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). For instructions on specifying binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
> [!NOTE]
>  When using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], setting the timeout to a large value does not impact the functionality of the adapter.  
  
## See Also  
[Troubleshoot the SQL adapter](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)