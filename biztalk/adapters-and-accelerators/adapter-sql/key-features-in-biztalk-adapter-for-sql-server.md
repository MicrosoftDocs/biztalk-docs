---
title: "Key features in BizTalk Adapter for SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6beab8d-c2c4-4add-860c-054b9aed8d70
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Key features in BizTalk Adapter for SQL Server
This section lists the features in [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)].  
  
> [!NOTE]
>  This topic has been used from the previous version of [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] Help.  
  
## Features in the SQL Adapter  
 Following are the features introduced in the previous releases of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
### Technology-Related Features  
  
|Feature|Comment|  
|-------------|-------------|  
|Use of Windows Communication Foundation (WCF)|The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is built on top of the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] ([!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]). In turn, the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is built on top of WCF. The adapter is exposed as a WCF channel to adapter clients. This enables connectivity, metadata exchange, and business data exchange with external systems.|  
|Support for the WCF channel model and the WCF service model|In the WCF channel model, adapter clients can consume the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] by directly sending and receiving XML messages. In the WCF service model, adapter clients can generate a .NET proxy class from the Web Services Description Language (WSDL) obtained by using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].|  
|Support for 64-bit platforms|The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is now available for 64-bit platforms.|  
  
### Metadata-Related Features  
  
|Feature|Comment|  
|-------------|-------------|  
|Browse, search, and retrieve metadata|The adapter clients can browse and search metadata in batches by specifying a batch size. This feature is available only when programming into the adapter and not through the Consume Adapter Service BizTalk Project Add-in. The metadata search is supported at the Tables, Views, Procedures, Scalar Functions, and Table Valued Functions levels. The search string is used directly within a SQL statement.|  
|Support for invoking artifacts with same name in different databases|In the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], the namespaces in the XML Schema Definition (XSD) file contained only the schema name, and in some cases the object name. However, if an application wants to execute operations on identically named artifacts with different metadata in different databases, the generated metadata will conflict. The only way to distinguish the metadata is to use the database name in the XSD namespaces.<br /><br /> The current version of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] allows you to specify the database name in the XSD namespaces by setting the value of the **UseDatabaseNameInXsdNamespace** binding property to TRUE. The default value of the binding property is false, which implies that the XSD namespaces will not contain the database name. For more information about the **UseDatabaseNameInXsdNamespace** binding property, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).|  
  
### Performance-Related Features  
  
|Feature|Comment|  
|-------------|-------------|  
|Support for performance counters|The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports WCF-based performance counters for use by adapter clients. For more information about performance counters, see [Use Performance Counters with the SQL adapter](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md).|  
  
### Operations-Related Features  
  
|Feature|Comment|  
|-------------|-------------|  
|Support for the SQL Server 2005 and SQL Server 2008 data types|The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports the following data types introduced in:<br /><br /> -   **SQL Server 2005**: XML, Varchar(Max), and Varbinary(Max).<br />-   **SQL Server 2008**: Date, Time, Datetimeoffset, Datetime2, Hierarchyid, Geography, Geometry, and FILESTREAM.|  
|Support for User-Defined Types (UDTs)|The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports performing operations on tables and views that contain UDTs. For information about support for UDTs, see [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md).|  
|Support for executing Transact-SQL and CLR stored procedures and functions|Adapter clients can execute Transact-SQL and CLR:<br /><br /> -   Stored procedures in a SQL Server database.<br />-   Scalar and table valued functions in a SQL Server database.<br /><br /> For more information about this, see [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx).|  
|Support for executing stored procedures with or without the FOR XML clause|The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables you to execute stored procedures that have a SELECT statement with or without a FOR XML clause. The previous version of the adapter supported only those stored procedures that had a FOR XML clause in the SELECT statement. For information about executing stored procedures, see [Execute Stored Procedures in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-the-sql-adapter.md).|  
|Support for streaming of large objects|Adapter clients can stream large character and binary fields in the SQL Server database using the Set\<column name\> operation, where <column_name> is the name of the column of type Varchar(Max), Nvarchar(Max) or Varbinary(Max). The Set\<column name\> operation also allows you to insert or update FILESTREAM data in a SQL Server 2008 database. For more information about this, see [Operations on Tables and Views That Contain Large Data Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md). **Note:**  To read character and binary fields in SQL Server tables and views, adapter clients use the Select operation.|  
|Support for query notifications|Adapter clients can receive query notifications from SQL Server based on a triggering SELECT statement or a stored procedure. The notification is sent by the SQL Server to the adapter clients as and when the result set for the SELECT statement or the stored procedure changes. For more information about query notifications, see [Receive  Query Notifications using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md).|  
|Support for executing arbitrary SQL statements|The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to execute arbitrary SQL statements using the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations. For more information about these operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).|  
|Support for composite operations|The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to perform composite operations on the SQL Server database. A composite operation can include any number of the following operations, and in any order:<br /><br /> -   The Insert, Update, and Delete operations on the tables and views.<br />-   Stored procedures that are surfaced as operations in the adapter.<br /><br /> For more information about composite operations, see [Message Schemas for Composite Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).|  
|Enhanced polling|The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] now supports two additional types of polling: **TypedPolling** and **XmlPolling**. For information about these polling types, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).|  
|Support for performing operations on artifacts in multiple schemas|Apart from the default schema (dbo), adapter clients can also perform operations on artifacts in other schemas in the SQL Server database provided that the user credentials used to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] has access to those schemas in the SQL Server database. For information about a schema in SQL Server database, see [http://go.microsoft.com/fwlink/?LinkId=130148](http://go.microsoft.com/fwlink/?LinkId=130148).|  
  
## See Also  
 [Overview of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)