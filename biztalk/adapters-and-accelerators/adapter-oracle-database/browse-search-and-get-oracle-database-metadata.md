---
title: "Browse, search, and get Oracle Database metadata | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MetadataExchange"
  - "metadata, searching"
  - "metadata, browsing"
  - "POLLINGSTMT"
  - "metadata, retrieving"
  - "IMetadataRetrievalContract"
  - "SQLEXECUTE"
ms.assetid: 828d5a8e-f0a3-47b4-8298-5571cff64b52
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Browse, search, and get Oracle Database metadata
The[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces metadata from the Oracle database that describes the message structure for communicating with the Oracle database using the adapter. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports two interfaces for retrieving metadata.  
  
- MetadataExchange provided by [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. WCF provides a metadata-exchange endpoint for all WCF bindings, which enables clients to get metadata from the Oracle database.  
  
- IMetadataRetrievalContract provided by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], which supports the metadata browsing and searching capabilities of the adapter.  
  
  The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces the Oracle database artifacts and respective operations that the adapter clients can invoke. The adapter also surfaces the SQLEXECUTE, POLLINGSTMT, and Notification operations that can be used to perform specific operations on the Oracle database. These operations are discussed later in this topic.  
  
  Adapter clients can browse, search, and retrieve metadata by using the WCF channel model, by using the WCF service model, or by creating a BizTalk project in Visual Studio. When using the WCF service model, you must use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the proxy classes for performing operations on the Oracle database. When using a BizTalk project, you must use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate metadata for the operations that you want to perform on the Oracle database. For more information about browsing, searching, and retrieving metadata using [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], see [Get metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).  
  
## Browsing Metadata  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables adapter clients to browse database tables, table views, stored procedures, functions, and packages that are available in the Oracle database. As part of the metadata browse operation, the adapter also surfaces the operations that can be performed on the Oracle database, including some custom operations supported by the adapters. These operations are available from the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces the following operations:  
  
 **Outbound Operations**  
  
 Contains a list of schemas in the underlying Oracle database. Expand a schema node to see the following artifacts:  
  
- **Table**: A list of all the tables in the schema. Select a table to view the Insert, Select, Update, and Delete operations.  
  
- **Procedure**: A list of stored procedures in the schema that are exposed as operations.  
  
- **Function**: A list of functions in the schema that are exposed as operations.  
  
- **Package**: A list of all the packages in the schema. Select a package to view the procedures and functions inside the package that are exposed as operations.  
  
- **View**: A list of all the views in the schema. Select a view to view the Insert, Select, Update, and Delete operations.  
  
  Apart from this, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] also exposes the **SQLEXECUTE** outbound operation, which enables the adapter clients to execute any generic data manipulation language (DML) or stored procedure in an Oracle database. The SQLEXECUTE operation is available when you select the root node (/). Note that the output of SQLEXECUTE is an array of data readers (output as array of generic records). As a result, any simple out parameters are not surfaced using the SQLEXECUTE operation. For more information about the operation, see [SQLEXECUTE Operation in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md).  
  
  **Inbound Operations**  
  
  Contains a list of schemas in the underlying Oracle database. Expand a schema node to see the following artifacts:  
  
- **Procedure**: A list of stored procedures in the schema that are exposed as operations for polling.  
  
- **Function**: A list of functions in the schema that are exposed as operations for polling.  
  
- **Package**: A list of packages in the schema. Select a package to view the packaged procedures and functions that are exposed as operations for polling.  
  
  Apart from this, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] also exposes the **POLLINGSTMT** and **Notification** inbound operations. The POLLINGSTMT operation enables adapter clients to obtain inbound data from the Oracle database based on a query polling mechanism supported by the adapter. The Notification operation enables adapter clients to register a SELECT statement as the notification query on the database, and the database sends a notification to the adapter client as and when the result set of the SELECT statement changes. The POLLINGSTMT and Notification operations are available when you select the root node (/). For more information about the operations, see [Support for Receiving Polling-based Data-changed Messages](../../adapters-and-accelerators/adapter-oracle-database/support-for-receiving-polling-based-data-changed-messages-in-oracle-database.md).md) and [Considerations for Receiving Database Changer Notifications Using the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md).  
  
  For more information about how the metadata is categorized, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).  
  
## Searching Metadata  
 With the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], it is possible to perform a search query on the Oracle database by using the Oracle search expressions that are compatible with the LIKE operator. For example, adapter clients can use a search expression such as “EMP%” to obtain tables starting with EMP. The adapter converts this to the following SQL query:  
  
```  
SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE 'EMP%' AND OWNER = 'SCOTT'  
```  
  
 Where, SCOTT is the schema with a collection of Oracle database artifacts.  
  
 The following table lists the special characters that can be used for search and their interpretation by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
|Special character|Interpretation|  
|-----------------------|--------------------|  
|_ (underscore)|Matches exactly one character<br /><br /> For example, A_ matches AB, AC, AD.|  
|% (percentage)|Matches zero or more characters.<br /><br /> For example, A% matches A, AB, ABC.|  
|\ (escape)|Escapes the special meaning of % and _<br /><br /> For example, A\\_B matches A_B.|  
  
> [!IMPORTANT]
>  The metadata search scope is restricted to the level immediately under the node at which the search operation is performed. For example, to search for a function, you must be searching under \\[Schema]\Functions. Recursive search is not supported.  
  
## Retrieving Metadata  
 When retrieving metadata, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] can extract metadata under a schema, including all or a subset of database objects with the respective object and operation parameters. The adapter presents the entities from the Oracle database as element names in XML. Because underscores are the only permissible special characters that can be included, all other special characters in the element names are encoded using underscores. For example, `emp$name` is encoded as `emp_x0024_name`.  
  
## See Also  
 [Overview of BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)   
 [Understand the BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)   
[Get metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)