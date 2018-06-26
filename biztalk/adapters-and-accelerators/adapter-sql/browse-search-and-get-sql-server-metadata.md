---
title: "Browse, search, and get SQL Server metadata | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 368dd5ca-456c-4cae-9e85-bcf504c4e7ed
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Browse, search, and get SQL Server metadata
The metadata that [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces from the SQL Server database describes the message structure for communicating with the SQL Server database using the adapter. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports two interfaces for retrieving metadata.  
  
- MetadataExchange provided by [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. WCF provides a metadata-exchange endpoint for all WCF bindings, which enables clients to get metadata from the SQL Server database.  
  
- IMetadataRetrievalContract provided by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], which supports the metadata browsing and searching capabilities of the adapter.  
  
  The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces the SQL Server database artifacts and respective operations that the adapter clients can invoke. The adapter also surfaces operations (such as ExecuteNonQuery, ExecuteReader, and ExecuteScalar) that can be used to perform specific operations on the SQL Server database. These operations are discussed later in this topic.  
  
> [!NOTE]
>  The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces artifacts in all the schemas in the SQL Server database that the currently connected user has access to. This implies that apart from the default schema (dbo), the adapter clients can also perform operations on artifacts in other schemas in the SQL Server database provided that the user credentials used to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] has access to those schemas in the SQL Server database. For information about a schema in SQL Server database, see [http://go.microsoft.com/fwlink/?LinkId=130148](http://go.microsoft.com/fwlink/?LinkId=130148).  
  
 You can use the adapter clients to browse, search, and retrieve metadata by:  
  
- Creating a BizTalk project in Visual Studio  
  
- Using the WCF service model  
  
- Using the WCF channel model  
  
  When using a BizTalk project, you must use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate metadata for the operations that you want to perform on the SQL Server database. When using the WCF service model, you must use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the proxy classes for performing operations on the SQL Server database. For more information about browsing, searching, and retrieving metadata using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Get metadata for SQL Server operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
## Browsing Metadata  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to browse database tables, views, stored procedures, and functions that are available in the SQL Server database. As part of the metadata browse operation, the adapter also surfaces the operations that can be performed on the SQL Server database, including some custom operations supported by the adapters. These operations are available from [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces the following operations:  
  
- The operations on tables, views, procedures, scalar functions, and table valued functions. For example, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] may surface Insert, Update, Select, and Delete operations for the EMPLOYEE table.  
  
- The Set\<column name\> operation for tables and views that enables adapter clients to write large data values in a streaming fashion. The Set operation is only returned for those tables and views that contain columns with any of the following data types: Varchar(Max), Nvarchar(Max) or Varbinary(Max). For more information, see [Operations on tables and views that contain large data types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md).  
  
- The ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations that enable adapter clients to execute arbitrary SQL statements in SQL Server. For more information about these operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
- The Polling and Notification operations to receive inbound messages from SQL Server. For information about the Polling operation, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md); for information about the Notification operation, see [Considerations for Receiving Query Notifications Using the SQL adapter](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md).  
  
  For more information about how the metadata is categorized, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md).  
  
## Searching Metadata  
 With the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], it is possible to perform a search query on the SQL Server database by using the SQL Server search expressions that are compatible with the LIKE operator. For example, adapter clients can use a search expression such as “EMP%” to obtain tables starting with EMP. The adapter converts this to the following SQL query:  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%'  
```  
  
 The following table lists the special characters that can be used for search and their interpretation by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
|Special character|Interpretation|  
|-----------------------|--------------------|  
|_ (underscore)|Matches exactly one character.<br /><br /> For example, “A_” matches “AB”, “AC”, “AD”.|  
|% (percentage)|Matches zero or more characters.<br /><br /> For example, “A%” matches “A”, “AB”, “ABC”.|  
|[ ]|-   Escapes the special meaning of _ and %.<br />-   Specifies a range or set of characters to be present.<br /><br /> For example:<br /><br /> -   %[%]% matches all names that include a % symbol.<br />-   [a-f] matches all names that have characters between and including ‘a’ and ‘f’.<br />-   [abc] matches all names that have characters ‘a’, ‘b’, and ‘c’.|  
|[^]|Specifies a range or set of characters not to be present.<br /><br /> For example:<br /><br /> -   [^a-f] matches all names that do not have characters between and including ‘a’ and ‘f’.<br />-   [^abc] matches all names that do not have characters ‘a’, ‘b’, and ‘c’.|  
  
> [!IMPORTANT]
>  The metadata search scope is restricted to the level immediately under the node at which the search operation is performed. For example, to search for a scalar function, you must be searching under /Scalar Function/[Schema]. Multi-level search is not supported.  
  
## Retrieving Metadata  
 When retrieving metadata, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can extract metadata under a schema, including all or a subset of database objects with the respective object and operation parameters. The adapter presents the entities from the SQL Server database as element names in XML. Because underscores are the only permissible special characters that can be included, all other special characters in the element names are encoded using underscores. For example, `emp$name` is encoded as `emp_x0024_name`.  
  
## See Also  
 [Overview of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)   
 [Understand BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)   
 [Get metadata for SQL Server operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)