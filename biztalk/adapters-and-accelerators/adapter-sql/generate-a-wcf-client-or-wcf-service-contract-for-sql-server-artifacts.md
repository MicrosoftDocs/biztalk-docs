---
title: "Generate a WCF Client or WCF Service Contract for SQL Server Artifacts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5fa7d8c0-8ee4-41e7-9394-d22e87e09391
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generate a WCF Client or WCF Service Contract for SQL Server Artifacts
You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class targeted at selected operations on SQL Server artifacts. You can also use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate the WCF client class; however, the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] exposes the functionality of the ServiceModel Metadata Utility Tool through a standard Microsoft Windows interface. It also provides browse and search capabilities that are not available with the svcutil.exe tool, and generates a configuration file based on the binding properties that you select when you connect to the SQL Server database.  
  
## Generating a WCF Client Class by Using the Add Adapter Service Reference Plug-in  
 Perform the following steps to generate a WCF client class by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click your project, and then click **Add Adapter Service Reference**.  
  
2. After the **Add Adapter Service Reference** dialog box opens, follow the steps in [Get metadata for SQL Server operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) to connect to SQL Server and to browse and search for operations. To create a WCF client class for the operations that you select, be sure that **Client (Outbound operations)** is selected from the **Select contract type** drop-down list. (This is the default).  
  
3. After you select all of the operations that you want to target, click **OK** to generate the WCF client class.  
  
   The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] adds two files to your project:  
  
- **The WCF client code file**. This file contains the generated WCF client class and helper code for the operations that you selected. The first time you run the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], it will generate this file with the default name **SQLAdapterBindingClient.cs**. If you run it again, the next file it generates will be called **SQLAdapterBindingClient1.cs**.  The number suffix will increase by 1 for every new file you generate.  You can also change the default prefix **SQLBinding** by entering a different prefix in the **Filename prefix** field of the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] before selecting **OK** to generate the file.  
  
- **App.config**. This file contains a binding configuration and client endpoint configurations that are based on the selections you made when you configured the connection for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
  > [!IMPORTANT]
  >  While using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the app.config file. You must manually add the binding property and its value in the app.config file, if required.  
  
## Generating a WCF Service Contract by Using the Add Adapter Service Reference Plug-in  
 For inbound operations such as polling the SQL Server database or receiving notifications from the database, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] either executes a query specified by the client application (in case of polling) or registers a query with SQL Server (in case of notification). In both the scenarios, the adapter sends the inbound message from SQL Server database to the consuming. In such a case, the consuming application acts as a service and the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] acts as the client. You must, therefore, implement a WCF service that can receive inbound operations from the adapter. To do this, you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a .NET interface that represents the service contract that is surfaced by the adapter for the inbound operations. This .NET interface is also called a WCF service contract. You then implement this interface to create the WCF service that you can use to receive the inbound operations.  
  
 Perform the following steps to generate a WCF service contract by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### To generate a WCF service contract for inbound operations  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Solution Explorer, right-click your project, and then click **Add Adapter Service Reference**.  
  
2. After the **Add Adapter Service Reference** dialog box opens, follow the steps in [Connect to SQL Server in Visual Studio Using Add Adapter Service Reference Plug-in](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-add-adapter-service-reference.md) to connect to the SQL Server database.  
  
   > [!IMPORTANT]
   >  If you are generating WCF service contract for **TypedPolling** inbound operation, you must specify the **InboundID** as part of the connection URI and **PollingStatement** binding property.  
  
3. After you have connected to the SQL Server database, select **Service (Inbound operations)** from the **Select contract type** drop-down list.  
  
4. In the **Select a category** box, click the root node (**/**), select the inbound operation from the **Available categories and operations** box, and then click **Add**.  
  
5. To generate the WCF service contract for the inbound operation, click **OK**.  
  
   The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] adds three files to your project:  
  
- **SqlAdapterBindingInterface.cs**. This file contains the generated WCF service contract (interface) and helper code for the inbound operation.  
  
- **SqlAdapterBindingService.cs**. This file contains a class that implements the interface defined in SqlAdapterBindingInterface.cs. You can implement the business logic that processes the records returned by the inbound operation.  
  
- **app.config**. This file contains a binding configuration, endpoint behaviors, and service endpoint configuration that are based on the selections you made when you configured the binding and connection for the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
  > [!IMPORTANT]
  >  While using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the app.config file. You must manually add the binding property and its value in the app.config file, if required.  
  
## Generating a WCF Client Class by Using svcutil.exe  
 You can use svcutil.exe to generate a WCF client class for your application. You must configure svcutil.exe to use it with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 Svcutil.exe generates the WCF client class in an output file with a default file name of **output.cs**. You must manually include this file in your [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] project. For more information about svcutil.exe, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).
  
## See Also  
[Develop SQL applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)