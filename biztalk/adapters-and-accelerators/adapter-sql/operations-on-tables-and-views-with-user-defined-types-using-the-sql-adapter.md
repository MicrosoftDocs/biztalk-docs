---
title: "Operations on tables and views with user-defined types using the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4006bbe-91ca-4cd9-844d-5ed63142001f
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on tables and views with user-defined types using the SQL adapter
You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform operations on tables or views that have columns of user-defined types (UDTs). You can use the standard table operations (Insert, Update, Delete, and Select) to read or write data into columns on UDT types. You can also execute stored procedures and functions on such tables. However, you need to perform certain tasks before you can use the adapter to operate on tables with UDT columns. Once you have performed these tasks, you can use the adapter to:  

-   Perform Insert, Delete, Update, and Select operations, as described in [Insert, update, delete, or select operations using BizTalk Server with the SQL adapter](../../adapters-and-accelerators/adapter-sql/insert-update-delete-or-select-using-the-sql-adapter-in-biztalk-server.md).  

-   Execute stored procedures, as described in [Execute stored procedures in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md).  

-   Perform composite operations on tables with UDT columns, as described in [Run composite operations on SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)  

-   Poll tables with UDT columns, as described in [Receive Polling-based Data-changed Messages from SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md).  

-   Perform other operations, as described in [Develop your BizTalk applications](../../core/develop-your-biztalk-applications.md).  

## Considerations While Performing Operations on Tables with UDTs  
 You must perform the following tasks before you can use the adapter to perform operations on tables with UDT columns.  

- **While generating schema for operation using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]**  


  |                       UDT Type                        |                                                                                                                                                                        Location of Assemblies                                                                                                                                                                        |
  |-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | UDTs shipped with SQL Server, for example, Geography  | -   Make sure Microsoft.SqlServer.Types.dll is added to the GAC.<br />-   Make sure SqlServerSpatial.dll is available in the System32 folder.<br /><br /> You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard. |
  | UDTs not shipped with SQL Server but defined by users |                      Make sure the respective assemblies for the UDTs are available at the same location as the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] executable, devenv.exe. The executable is typically available at `<installation drive>:\Program Files\Microsoft Visual Studio <version>\Common7\IDE`.                      |


- **While performing the operation using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]**  


  |                       UDT Type                        |                                                                                                                                                                        Location of Assemblies                                                                                                                                                                        |
  |-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | UDTs shipped with SQL Server, for example, Geography  | -   Make sure Microsoft.SqlServer.Types.dll is added to the GAC.<br />-   Make sure SqlServerSpatial.dll is available in the System32 folder.<br /><br /> You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard. |
  | UDTs not shipped with SQL Server but defined by users |                                     Make sure the respective assemblies for the UDTs are available under the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] installation location. For BizTalk Server, typically this is \<installation drive\>:\Program Files\Microsoft BizTalk Server.                                      |


- **While performing the operation using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]**  

  |UDT Type|Location of Assemblies|  
  |--------------|----------------------------|  
  |UDTs shipped with SQL Server, for example, Geography|-   Make sure Microsoft.SqlServer.Types.dll is added to the GAC.<br />-   Make sure SqlServerSpatial.dll is available in the System32 folder.<br /><br /> You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard.|  
  |UDTs not shipped with SQL Server but defined by users|Make sure the respective assemblies for the UDTs are available at the same location as the project executable file, which typically is under the project’s \bin\Debug folder.|  

  Once you have completed these tasks, you are all set to perform operations on tables with UDTs.  

## See Also  
 [Connect to an SAP system using the adapter](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)