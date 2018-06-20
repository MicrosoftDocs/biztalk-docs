---
title: "Overview of the WCF service model with the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7641bcc7-3845-4914-9b1b-cb86b998ea6d
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Overview of the WCF service model with the SQL adapter
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes a SQL Server operation as a WCF service. To perform operations on SQL Server artifacts, for example to invoke a stored procedure, you invoke an operation on the adapter, which, in turn, performs the operation on the SQL Server. Your code therefore acts as a client to the WCF service presented by the adapter.  
  
 In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes. These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface. A client application can call the methods of the WCF client class to invoke operations on the adapter. To implement a service to receive inbound operations from the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you implement the interface generated for the inbound operations.  
  
 The following section explains how to use the WCF service model to invoke operations with a WCF client.  
  
## Invoking Operations on the SQL Server with a WCF Client  
 To use the WCF service model to invoke operations on the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must first generate a WCF client class for the target operations. You can then create an instance of this class, a WCF client, and call its methods to perform these operations on the SQL Server system. This section provides an outline of how a typical .NET adapter client application looks like. Detailed explanations on how to perform different operations on the SQL Server database using the adapter are provided in specific topics.  
  
#### To invoke operations on the SQL adapter  
  
1. Generate a WCF client class and helper code. Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]to generate a WCF client class targeted at the SQL Server database artifacts with which you want to work. For more information about how to generate a WCF client, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
2. Create a WCF client instance and configure the WCF client. Configuring the WCF client involves specifying the binding and endpoint address (connection URI) that the client will use. You can do this either imperatively in code or declaratively in configuration. The following code creates a WCF client that targets the **Select** operation on the **Employee** table in a SQL Server database. It also sets the credentials for the SQL Server database. The WCF client is initialized from configuration.  
  
   ```  
   TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee"); //picking the binding and address from the app.config  
  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  
  
   > [!NOTE]
   >  You can either specify the client binding and endpoint address in the code or declare it in the app.config configuration file. The preceding code snippet uses the latter. For more information on how to use either approaches, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).  
  
3. Open the WCF client.  
  
   ```  
   client.Open();  
   ```  
  
4. Invoke methods on the WCF client created in preceding step to perform a Select operation on the SQL server database. The following code invokes the Select method of the WCF client to invoke the SELECT statement on a SQL Server database table.  
  
   ```  
   client.Select("*", "where [Name] = ‘John Smith’");  
   ```  
  
5. Close the WCF client.  
  
   ```  
   client.Close();  
   ```  
  
## See Also  
[Develop SQL applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)