---
title: "Run Operations on Tables and Views with Large Data Types in SQL using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d33e17c-e09e-4a57-9acc-43095e67ed8c
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Run Operations on Tables and Views with Large Data Types in SQL using the WCF Service Model
The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to read and update data in columns of large data types, that is, varchar(max), nvarchar(max), or varbinary(max). To read data from such columns, adapter clients can use the Select operation. To insert or update data into such columns, the adapter exposes a Set\<*column_name*\> operation, where \<*column_name*\> is the name of the column of type varchar(max), nvarchar(max), or varbinary(max).  
  
 Additionally, in SQL Server, you can have the varbinay(max) column store unstructured data such as text documents and images. Such unstructured data is called FILESTREAM data. FILESTREAM data can be stored as files on the file system. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables the client to enter FILESTREAM data into columns of type varbinary(max). [FILESTREAM storage](https://docs.microsoft.com/sql/relational-databases/blob/filestream-sql-server) has more information. 
  
 This topic provides information about certain tasks you must perform on the computer running SQL Server and the computer running the adapter client to be able to insert or update FILESTREAM data. This topic also provides instructions on performing Set\<*column_name*\> operations to insert FILESTREAM data.  
  
> [!NOTE]
>  If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md).  
  
## Prerequisites  
 You must perform the following tasks on the computer running SQL Server and the computer running the adapter client.  
  
- **On the computer running SQL Server**  
  
  -   You must enable FILESTREAM on the SQL Server instance. See [Enable and Configure FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/enable-and-configure-filestream).
  
  -   You must create a FILESTREAM-enabled database. See [Create a FILESTREAM-Enabled Database](https://docs.microsoft.com/sql/relational-databases/blob/create-a-filestream-enabled-database).
  
  -   You must have a table for storing FILESTREAM data. See [Create a Table for Storing FILESTREAM Data](https://docs.microsoft.com/sql/relational-databases/blob/create-a-table-for-storing-filestream-data),
  
- **On the computer running the adapter client**  
  
  -   You must have the SQL Client Connectivity SDK installed. You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard. The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.  
  
  After you have completed these tasks, you are all set to insert or update FILESTREAM data in SQL Server database tables.  
  
## How This Topic Demonstrates Operations on Large Data Types  
 To demonstrate how to perform Set\<*column_name*\> operations on tables with large data types, take a table, **Records**, that has columns **Id** and **Document**:  
  
-   The **Records** table, with all the data, is created by running the SQL script provided with the samples. For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
-   The **Id** column is of type uniqueidentifier and takes a GUID. Assume that the **Id** column already has a GUID ‘`438B7B4C-5491-409F-BCC1-78817C399EC3`’.  
  
-   The **Document** column is of type VARBINARY(MAX). To update the **Document** column, the adapter exposes the **SetDocument** operation.  
  
> [!NOTE]
>  For SQL Server, to demonstrate FILESTREAM operations, assume that the **Document** column can store FILESTREAM data.  
  
## About the Examples Used in this Topic  
 The example in this topic performs operations on the **Records** table. The **Records** table is created by running the SQL script provided with the samples. For more information about samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md). A sample, **Records_FILESTREAM_Op**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.  
  
## The WCF Client Class  
 The name of the WCF client generated for the operations on large data types that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers, is based on the name of the table or view, as listed in the following table.  
  
|SQL Server Database Artifact|WCF Client Name|  
|----------------------------------|---------------------|  
|Table|TableOp_[Schema]_[TABLE_NAME]Client|  
|View|ViewOp_[Schema]_[VIEW_NAME]Client|  
  
 [SCHEMA] = Collection of SQL Server artifacts; for example, dbo.  
  
### Method Signature for Invoking Operations on Columns of Large Data Types  
 The following table shows the method signatures for the basic operations on a table. The signatures are the same for a view, except that the view namespace and name replace those of the table.  
  
|Operation|Method Signature|  
|---------------|----------------------|  
|Set\<*column_name*\>|public void Set\<*column_name*\>(string Filter, byte[] Data);|  
  
 \<*column_name*\> = Name of the column of large data type.  
  
 As an example, the following code shows the method signatures for a WCF client class generated for the **SetDocument** operation on the **Records** table under the default “dbo” schema.  
  
```  
public partial class TableOp_dbo_RecordsClient : System.ServiceModel.ClientBase<TableOp_dbo_Records>, TableOp_dbo_Records {      
    public void SetDocument (string Filter, byte[] Data);  
}  
```  
  
 In this snippet, **TableOp_dbo_RecordsClient** is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
### Parameters for Operations on Columns of Large Data Types  
 This section provides the parameters required by the Set\<*column_name*\> operation.  
  
|Parameter name|Description|  
|--------------------|-----------------|  
|string Filter|Specifies the WHERE clause based on which the adapter updates the record for the column of large data type.|  
|byte[] Data|Specifies the value that must be updated for the column of large data type.|  
  
 The Set\<*column_name*\> operation does not return any values.  
  
## Creating a WCF Client to Invoke Operations on Columns of Large Data Types  
 The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md). This section describes how to create a WCF client to invoke the **SetDocument** operation on the **Records** table. The adapter exposes the **SetDocument** operation to update data in columns of large data types.  
  
#### To create a WCF client  
  
1. Create a Visual C# project in Visual Studio. For this topic, create a console application.  
  
2. Generate the WCF client class for the **SetDocument** operation on the **Records** table. For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
3. In the Solution Explorer, add reference to `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, and `System.Transactions`.  
  
4. Open the Program.cs file and add the `System.Transactions` namespace.  
  
5. In the Program.cs, create a client as described in the snippet below.  
  
   ```  
  
             TableOp_dbo_RecordsClient client = new TableOp_dbo_RecordsClient("SqlAdapterBinding_TableOp_dbo_Records");  
   client.ClientCredentials.UserName.UserName = "";  
   client.ClientCredentials.UserName.Password = "";  
  
   ```  
  
    In this snippet, `TableOp_dbo_RecordsClient` is the WCF client defined in SqlAdapterBindingClient.cs. This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. `SqlAdapterBinding_TableOp_dbo_Records` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.  
  
   > [!CAUTION]
   >  To perform operations on FILESTREAM data, you must always connect to SQL Server using Windows authentication. To connect using Windows authentication, you must provide empty username and password, as shown in the preceding snippet. Also, before using Windows authentication to connect to SQL Server, you must have performed the steps mentioned in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
   > [!NOTE]
   >  In this snippet, you use the binding and endpoint address from the configuration file. You can also explicitly specify these values in your code. For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).  
  
6. Open the client as described in the snippet below:  
  
   ```  
   try  
   {  
      Console.WriteLine("Opening Client...");  
      client.Open();  
   }  
   catch (Exception ex)  
   {  
      Console.WriteLine("Exception: " + ex.Message);  
      throw;  
   }  
   ```  
  
7. Invoke the **SetDocument** operation on the **Records** table.  
  
   > [!CAUTION]
   >  The Set<em><column_name></em> operations must always be performed in a transaction. To ensure this, the Set<em><column_name></em> operation must be invoked within a transaction scope and the **UseAmbientTransaction** binding property must be set to **true** in the app.config.  
  
   ```  
   using (TransactionScope tx = new TransactionScope())  
   {  
       string filter = "WHERE Id='438B7B4C-5491-409F-BCC1-78817C399EC3'";  
       byte[] data = ASCIIEncoding.ASCII.GetBytes("Sample data");  
       client.SetDocument(filter, data);  
       tx.Complete();  
   }  
   ```  
  
    Here, the application converts the string “Sample data” into a base64 encoded string, and updates it in the record that satisfies the filter criteria.  
  
8. Close the client as described in the snippet below:  
  
   ```  
   client.Close();  
   Console.WriteLine("Press any key to exit...");  
   Console.ReadLine();  
   ```  
  
9. Build the project and then run it. The application updates the **Document** column in the **Records** table.  
  
## See Also  
[Develop applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)