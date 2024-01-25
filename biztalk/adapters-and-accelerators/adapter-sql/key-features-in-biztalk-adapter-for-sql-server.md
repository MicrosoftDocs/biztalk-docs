---
title: "Key features in BizTalk Adapter for SQL Server"
description: Learn more about the features of the SQL Server adapter in BizTalk Server, including WCF, metadata, executing stored procedures, streaming large objects, and more.
ms.custom: "biztalk-2020"
ms.date: "01/13/2020"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Features in BizTalk Adapter for SQL Server

This article lists the features included in the Microsoft BizTalk Adapter for SQL Server.

## Technology features

- **Use Windows Communication Foundation (WCF)**: The SQL adapter is built on top of the Microsoft Windows Communication Foundation (WCF) Line of Business (LOB) Adapter SDK (WCF LOB Adapter SDK). In turn, the WCF LOB Adapter SDK is built on top of WCF. The adapter is exposed as a WCF channel to adapter clients. This enables connectivity, metadata exchange, and business data exchange with external systems.
- **WCF channel model and the WCF service model**: In the WCF channel model, adapter clients can consume the SQL adapter by directly sending and receiving XML messages. In the WCF service model, adapter clients can generate a .NET proxy class from the Web Services Description Language (WSDL) obtained by using the SQL adapter.
- **64-bit platform support**: The SQL adapter is available for 64-bit platforms.

## Metadata features

- **Browse, search, and retrieve metadata**: The adapter clients can browse and search metadata in batches by specifying a batch size. This feature is available only when programming into the adapter and not through the Consume Adapter Service BizTalk Project Add-in. The metadata search is supported at the Tables, Views, Procedures, Scalar Functions, and Table Valued Functions levels. The search string is used directly within a SQL statement.\
- **Invoke artifacts with same name in different databases**: In the SQL adapter, the namespaces in the XML Schema Definition (XSD) file contained only the schema name, and in some cases the object name. However, if an application wants to execute operations on identically named artifacts with different metadata in different databases, the generated metadata will conflict. The only way to distinguish the metadata is to use the database name in the XSD namespaces.

  The current version of the SQL adapter allows you to specify the database name in the XSD namespaces by setting the value of the **UseDatabaseNameInXsdNamespace** binding property to TRUE. The default value of the binding property is false, which implies that the XSD namespaces will not contain the database name.

  For more information about the **UseDatabaseNameInXsdNamespace** binding property, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).

## Performance feature

- **Performance counters**: The SQL adapter supports WCF-based performance counters for use by adapter clients.

  For more information, see [Use Performance Counters with the SQL adapter](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md).

## Operations features

- **SQL Server 2005 and SQL Server 2008 data types**: The SQL adapter supports the following data types introduced in:
  - **SQL Server 2005**: XML, Varchar(Max), and Varbinary(Max)
  - **SQL Server 2008**: Date, Time, Datetimeoffset, Datetime2, Hierarchyid, Geography, Geometry, and FILESTREAM.
- **User-Defined Types (UDTs)**: The SQL adapter supports performing operations on tables and views that contain UDTs. For information about support for UDTs, see [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md).
- **Execute Transact-SQL and CLR stored procedures and functions**: Adapter clients can execute Transact-SQL and CLR:
  - Stored procedures in a SQL Server database
  - Scalar and table valued functions in a SQL Server database
x
  For more information, see [operations supported by the SQL adapter](../../adapters-and-accelerators/adapter-sql/what-operations-are-supported-by-the-sql-adapter.md).

- **Execute stored procedures with or without the FOR XML clause**: The SQL adapter enables you to execute stored procedures that have a SELECT statement with or without a FOR XML clause. Older versions of the adapter supported only those stored procedures that had a FOR XML clause in the SELECT statement. For information about executing stored procedures, see [Execute Stored Procedures in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-the-sql-adapter.md).
- **Stream large objects**: Adapter clients can stream large character and binary fields in the SQL Server database using the `Set\<column name\>` operation, where `<column_name>` is the name of the column of type Varchar(Max), Nvarchar(Max) or Varbinary(Max). The `Set\<column name\>` operation also allows you to insert or update FILESTREAM data in a SQL Server 2008 database.

  For more information, see [Operations on Tables and Views That Contain Large Data Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md).

  To read character and binary fields in SQL Server tables and views, adapter clients should use the Select operation.

- **Query notifications**: Adapter clients can receive query notifications from SQL Server based on a triggering SELECT statement or a stored procedure. The notification is sent by the SQL Server to the adapter clients as and when the result set for the SELECT statement or the stored procedure changes.

  For more information, see [Receive  Query Notifications using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md).

- **Execute arbitrary SQL statements**: The SQL adapter enables adapter clients to execute arbitrary SQL statements using the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations.

  For more information, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).

- **Composite operations**: The SQL adapter enables adapter clients to perform composite operations on the SQL Server database. A composite operation can include any number of the following operations, and in any order:
  - The Insert, Update, and Delete operations on the tables and views.
  - Stored procedures that are surfaced as operations in the adapter.

  For more information, see [Message Schemas for Composite Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).

- **Enhanced polling**: The SQL adapter supports two additional types of polling: **TypedPolling** and **XmlPolling**. For information about these polling types, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).
- **Run operations on artifacts in multiple schemas**: Apart from the default schema (dbo), adapter clients can execute operations on artifacts in other schemas in the SQL Server database. The user credentials used to connect using the SQL adapter must have access to those schemas in the SQL Server database.

  For more information, see [SQL Server database schemas](/previous-versions/sql/sql-server-2008-r2/ms365789(v=sql.105)).

- **[Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine)**: The SQL Adapter can query SQL Server Always Encrypted columns. The **ColumnEncryptionSetting** binding property enables or disables the functionality to get decrypted/encrypted column values from an Always Encrypted database.

  When the ColumnEncryptionSetting binding is set to **Disabled** (default), the SQL adapter disables Always Encrypted for the query. When set to **Enabled**, the SQL adapter [enables Always Encrypted for the query](/dotnet/api/system.data.sqlclient.sqlcommandcolumnencryptionsetting).

  This feature applies to:

  - BizTalk Server 2020 and newer
  - BizTalk Server 2016 Feature Pack 1 and newer

## See Also

 [Overview of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)