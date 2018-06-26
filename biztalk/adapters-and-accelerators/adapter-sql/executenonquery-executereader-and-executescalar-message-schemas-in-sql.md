---
title: "Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51f8cb98-8da8-40c1-bf87-4aad5a24bba2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes the ExecuteNonQuery, ExecuteReader, and ExecuteScalar outbound operations at the root level to execute any arbitrary SQL statements in SQL Server.  
  
 For more information about:  
  
- These operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
- Performing these operations using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
## Message Structure for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations  
 The messages in these operations follow a request-response message exchange pattern, and the following table shows the structure of these request and response messages.  
  
|Operation|XML Message|Description|  
|---------------|-----------------|-----------------|  
|ExecuteNonQuery Request|`<ExecuteNonQuery xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">    <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query>  </ExecuteNonQuery>`|Within the `<Query>` tag, you can specify multiple PL/SQL statements separated by a semi-colon.|  
|ExecuteNonQuery Response|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQueryResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteNonQueryResult>[value]</ExecuteNonQueryResult> </ExecuteNonQueryResponse>`|For the UPDATE, INSERT, and DELETE statements, `[value]` represents the number of rows affected by the PL/SQL statements in the *ExecuteNonQuery Request* message. For all other types of statements, `[value]` is -1.|  
|ExecuteReader Request|`<ExecuteReader xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query> </ExecuteReader>`|Within the `<Query>` tag, you can specify multiple PL/SQL statements separated by a semi-colon.|  
|ExecuteReader Response|`<?xml version="1.0" encoding="utf-8" ?>  <ExecuteReaderResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteReaderResult>     <DataSet>       <Any>[value]</Any>       <Any>[value]</Any>       …     </DataSet>   </ExecuteReaderResult> </ExecuteReaderResponse>`|The result set is the response message of the PL/SQL statements executed in the *ExecuteReader Request* message, and is returned as an array of DataSet. For information about DataSet, see “DataSet Class” at [http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853).|  
|ExecuteScalar Request|`<ExecuteScalar xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query> </ExecuteScalar>`|Within the `<Query>` tag, you can specify multiple PL/SQL statements separated by a semi-colon.|  
|ExecuteScalar Response|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalarResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteScalarResult>[value]</ExecuteScalarResult> </ExecuteScalarResponse>`|The `[value]` represents the value in the first column of the first row in the result set returned by the PL/SQL statements in the *ExecuteScalar Request* message.|  
  
 [PL/SQL STATEMENT] = The entire PL/SQL statement to be executed.  
  
## Message Action for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations  
 The following table shows the message actions that are used by the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations.  
  
|Operation|Action|  
|---------------|------------|  
|ExecuteNonQuery Request|GenericOp/ExecuteNonQuery|  
|ExecuteNonQuery Response|GenericOp/ExecuteNonQuery/response|  
|ExecuteReader Request|GenericOp/ExecuteReader|  
|ExecuteReader Response|GenericOp/ExecuteReader/response|  
|ExecuteScalar Request|GenericOp/ExecuteScalar|  
|ExecuteScalar Response|GenericOp/ExecuteScalar/response|  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)