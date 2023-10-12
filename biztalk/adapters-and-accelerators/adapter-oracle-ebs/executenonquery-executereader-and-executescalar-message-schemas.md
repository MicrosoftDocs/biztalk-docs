---
description: "Learn about the message schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations used by the Microsoft BizTalk Adapter for Oracle E-Business Suite."
title: "Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations1"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations Message Schemas

The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes the ExecuteNonQuery, ExecuteReader, and ExecuteScalar outbound operations at the root level to execute any arbitrary SQL statements or PL/SQL blocks in Oracle E-Business Suite.  
  
 For more information about:  
  
- These operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
- Performing these operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
## Message Structure for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations
  
The messages in these operations follow a request-response message exchange pattern, and the following table shows the structure of these request and response messages.  
  
> [!NOTE]
> See entity descriptions after the table.  
  
|Operation|XML Message|  
|---------------|-----------------|  
|ExecuteNonQuery Request|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQuery xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query>   <OutputRefCursorNames>     <string>[stringvalue1]</string>     <string>[stringvalue2]</string>     …   </OutputRefCursorNames> </ExecuteNonQuery>`|  
|ExecuteNonQuery Response|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQueryResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteNonQueryResult>[value]</ExecuteNonQueryResult>   <OutputRefCursors>     <DataSet>       <Any>[value]</Any>       <Any>[value]</Any>       …     </DataSet>   </OutputRefCursors> </ExecuteNonQueryResponse>`|  
|ExecuteReader Request|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReader xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteReader>`|  
|ExecuteReader Response|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReaderResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteReaderResult>     <Any>[value]</Any>     <Any>[value]</Any>       …   </ExecuteReaderResult> </ExecuteReaderResponse>`|  
|ExecuteScalar Request|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalar xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteScalar>`|  
|ExecuteScalar Response|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalarResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteScalarResult>[value]</ExecuteScalarResult> </ExecuteScalarResponse>`|  
  
 Entity descriptions:  
  
 [PL/SQL block] = The entire PL/SQL block to be executed.  
  
 [stringvalue1] = A value in the array of strings.  
  
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
