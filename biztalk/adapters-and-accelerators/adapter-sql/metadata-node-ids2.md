---
title: "Metadata Node IDs for the SQL adapter in BizTalk Adapter Pack | Microsoft Docs"
description: Metadata, search, retrieval nodes types and IDs used in SQL components that are exposed in SQL Server adapter - BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8601a328-5380-4577-a121-c926e0fd3140
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Node types and IDs for the SQL Server adapter

## Metadata Node IDs
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces SQL Server database artifacts in a hierarchical manner. The following table lists the node types and node IDs for SQL Server database artifacts that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces. The node ID is the absolute path of the node that is used in the **IMetadataRetrievalContractBrowse**, **Search**, and **GetMetadata** methods.  


| Artifact Display Name  |     Node Type      |                        Node ID                         |                    Example                     |                                                                                                                                                    Description                                                                                                                                                    |
|------------------------|--------------------|--------------------------------------------------------|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           --           |      CATEGORY      |                           /                            |                       /                        | [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] root node. Returns all first-level nodes; this includes the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operation nodes and all schema nodes for the outbound operations, and the Polling operation node for the inbound operation. |
|    ExecuteNonQuery     | OUTBOUND OPERATION |               GenericOp/ExecuteNonQuery                |           GenericOp/ExecuteNonQuery            |                                                                                                                  ExecuteNonQuery operation node. Returns WSDL for the ExecuteNonQuery operation.                                                                                                                  |
|     ExecuteReader      | OUTBOUND OPERATION |                GenericOp/ExecuteReader                 |            GenericOp/ExecuteReader             |                                                                                                                    ExecuteReader operation node. Returns WSDL for the ExecuteReader operation.                                                                                                                    |
|     ExecuteScalar      | OUTBOUND OPERATION |                GenericOp/ExecuteScalar                 |            GenericOp/ExecuteScalar             |                                                                                                                    ExecuteScalar operation node. Returns WSDL for the ExecuteScalar operation.                                                                                                                    |
|        Polling         | INBOUND OPERATION  |                        Polling                         |                    Polling                     |                                                                                                                          Polling operation node. Returns WSDL for the Polling operation.                                                                                                                          |
|      Notification      | INBOUND OPERATION  |                      Notification                      |                  Notification                  |                                                                                                                     Notification operation node. Returns WSDL for the Notification operation.                                                                                                                     |
|       Procedures       |      CATEGORY      |                      Procedures/                       |                  Procedures/                   |                                                                                                                     Schema procedures node. Returns all procedures for the specified schema.                                                                                                                      |
|     [DB_PROCEDURE]     | OUTBOUND OPERATION |         Procedure/[DB_SCHEMA]/[Procedure_Name]         |         Procedure/dbo/ADD_EMP_DETAILS          |                                                                                                                           Procedure node. Returns the WSDL for the specified procedure.                                                                                                                           |
|         Tables         |      CATEGORY      |                        Tables/                         |                    Tables/                     |                                                                                                                       Schema tables node. Returns all table nodes for the specified schema.                                                                                                                       |
|       [DB_TABLE]       |      CATEGORY      |                           -                            |                       -                        |                   Table node. Returns all operation nodes (Insert, Select, Update, Delete, and Set) for the specified table.<br /><br /> The Set operation is only returned for tables that contain columns with any of the following data type: Varchar(Max), Nvarchar(Max) or Varbinary(Max).                   |
|         Insert         | OUTBOUND OPERATION |         TableOp/Insert/[DB_SCHEMA]/[DB_TABLE]          |          TableOp/Insert/dbo/Employee           |                                                                                                            Table Insert operation node. Returns WSDL for the Insert operation for the specified table.                                                                                                            |
|         Select         | OUTBOUND OPERATION |         TableOp/Select/[DB_SCHEMA]/[DB_TABLE]          |          TableOp/Select/dbo/Employee           |                                                                                                            Table Select operation node. Returns WSDL for the Select operation for the specified table.                                                                                                            |
|         Update         | OUTBOUND OPERATION |         TableOp/Update/[DB_SCHEMA]/[DB_TABLE]          |          TableOp/Update/dbo/Employee           |                                                                                                            Table Update operation node. Returns WSDL for the Update operation for the specified table.                                                                                                            |
|         Delete         | OUTBOUND OPERATION |         TableOp/Delete/[DB_SCHEMA]/[DB_TABLE]          |          TableOp/Delete/dbo/Employee           |                                                                                                            Table Delete operation node. Returns WSDL for the Delete operation for the specified table.                                                                                                            |
|    Set[COLUMN_NAME]    | OUTBOUND OPERATION | TableOp/WriteText/[DB_SCHEMA]/[DB_TABLE]/[COLUMN_NAME] | TableOp/WriteText/dbo/Employee/Job_Description |                                          Table Set operation node. Returns WSDL for the Set operation for the specified column in the table. (Only surfaced if the table contains columns with any of the following data type: (Max), Nvarchar(Max) or Varbinary(Max)).                                           |
|         Views          |      CATEGORY      |                         Views/                         |                     Views/                     |                                                                                                                        Schema views node. Returns all view nodes for the specified schema.                                                                                                                        |
|       [DB_VIEW]        |      CATEGORY      |                           -                            |                       -                        |                                                                                                        View node. Returns all operation nodes (Insert, Select, Update, and Delete) for the specified view.                                                                                                        |
|         Insert         | OUTBOUND OPERATION |          ViewOp/Insert/[DB_SCHEMA]/[DB_VIEW]           |        ViewOp/Insert/dbo/Employee_View         |                                                                                                             View Insert operation node. Returns WSDL for the Insert operation for the specified view.                                                                                                             |
|         Select         | OUTBOUND OPERATION |          ViewOp/Select/[DB_SCHEMA]/[DB_VIEW]           |        ViewOp/Select/dbo/Employee_View         |                                                                                                             View Select operation node. Returns WSDL for the Select operation for the specified view.                                                                                                             |
|         Update         | OUTBOUND OPERATION |          ViewOp/Update/[DB_SCHEMA]/[DB_VIEW]           |        ViewOp/Update/dbo/Employee_View         |                                                                                                             View Update operation node. Returns WSDL for the Update operation for the specified view.                                                                                                             |
|         Delete         | OUTBOUND OPERATION |          ViewOp/Delete/[DB_SCHEMA]/[DB_VIEW]           |        ViewOp/Delete/dbo/Employee_View         |                                                                                                             View Delete operation node. Returns WSDL for the Delete operation for the specified view.                                                                                                             |
|    Scalar Functions    |      CATEGORY      |                    ScalarFunctions/                    |                ScalarFunctions/                |                                                                                                               Schema scalar functions node. Returns all scalar functions for the specified schema.                                                                                                                |
|   [DB_SCLR_FUNCTION]   | OUTBOUND OPERATION |     ScalarFunction/[DB_SCHEMA]/[DB_SCLR_FUNCTION]      |         ScalarFunction/dbo/GET_EMP_ID          |                                                                                                                     Scalar function node. Returns the WSDL for the specified scalar function.                                                                                                                     |
| Table Valued Functions |      CATEGORY      |                    TableFunctions/                     |                TableFunctions/                 |                                                                                                         Schema table valued functions node. Returns all table valued functions for the specified schema.                                                                                                          |
|   [DB_TBL_FUNCTION]    | OUTBOUND OPERATION |      TableFunction/[DB_SCHEMA]/[DB_TBL_FUNCTION]       |         TableFunction/dbo/TVF_EMPLOYEE         |                                                                                                               Table valued function node. Returns the WSDL for the specified table valued function.                                                                                                               |

 [DB_SCHEMA] = Collection of SQL Server artifacts; for example, dbo.  

 [DB_TABLE] = The name of an SQL Server table; for example, Employee.  

 [DB_VIEW] = The name of an SQL Server view; for example, Employee_View.  

 [DB_PROCEDURE] = The name of an SQL Server stored procedure; for example, ADD_EMP_DETAILS.  

 [DB_SCLR_FUNCTION] = The name of an SQL Server scalar function; for example, GET_EMP_ID.  

 [DB_TBL_FUNCTION] = The name of an SQL Server table valued function; for example, TVF_EMPLOYEE.  

## Metadata Search and Node IDs  
 Metadata search is a powerful feature that the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] surfaces as part of its **MetadataRetrievalContract** interface. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses this feature to support searching on the following SQL Server artifacts. The metadata search scope is restricted to the level immediately under the node at which the search operation is performed. For example, to search for a scalar function, you must be searching under /Scalar Function/[Schema]. Recursive search is not supported.  

|Artifact|Node ID|Node Type Returned|Description|  
|--------------|-------------|------------------------|-----------------|  
|/ (i.e. Root node)|/|CATEGORY|Return all schema nodes that match the search expression.|  
|[DB_PROCEDURE]|/Procedure/[DB_SCHEMA]|OUTBOUND OPERATION|Return all procedure nodes in the specified schema that match the search expression.|  
|[DB_TABLE]|/Table/[DB_SCHEMA]|CATEGORY|Return all table nodes in the specified schema that match the search expression.|  
|[DB_VIEW]|/View/[DB_SCHEMA]|CATEGORY|Return all view nodes in the specified schema that match the search expression.|  
|[DB_SCLR_FUNCTION]|/ScalarFunction/[DB_SCHEMA]|OUTBOUND OPERATION|Return all scalar function nodes in the specified schema that match the search expression.|  
|[DB_TBL_FUNCTION]|/TableFunction/[DB_SCHEMA]|OUTBOUND OPERATION|Return all table valued function nodes in the specified schema that match the search expression.|  

 [DB_SCHEMA] = Collection of SQL Server artifacts; for example, dbo.  

 [DB_TABLE] = The name of an SQL Server table; for example, Employee.  

 [DB_VIEW] = The name of an SQL Server view; for example, Employee_View.  

 [DB_PROCEDURE] = The name of an SQL Server procedure; for example, ADD_EMP_DETAILS.  

 [DB_SCLR_FUNCTION] = The name of an SQL Server scalar function; for example, GET_EMP_ID.  

 [DB_TBL_FUNCTION] = The name of an SQL Server table valued function; for example, TVF_EMPLOYEE.  

 You can specify search expressions that are compatible with any valid expression that can be used for the SQL Server LIKE operator. For example, to perform a search on the tables contained in a schema, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] executes the following SQL: `SELECT TABLE_NAME FROM ALL_TABLES WHERE TABLE_NAME LIKE ‘[SEARCH_STR]’`.  

 The following table lists the special characters that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports in search expressions.  

|Special Character|Interpretation|  
|-----------------------|--------------------|  
|% (percentage)|Matches zero or more characters.<br /><br /> For example, "A%" matches "A", "AB", "ABC", and so on.|  
|_ (underscore)|Matches exactly 1 character.<br /><br /> For example, "A_" matches "AB", "AC", "AD", and so on.|  
|[ ]|-   Escapes the special meaning of _ and %.<br />-   Specifies a range or set of characters to be present.<br /><br /> For example:<br /><br /> -   %[%]% matches all names that include a % symbol.<br />-   [a-f] matches all names that have characters between and including ‘a’ and ‘f’.<br />-   [abc] matches all names that have characters ‘a’, ‘b’, and ‘c’.|  
|[^]|Specifies a range or set of characters not to be present.<br /><br /> For example:<br /><br /> -   [^a-f] matches all names that do not have characters between and including ‘a’ and ‘f’.<br />-   [^abc] matches all names that do not have characters ‘a’, ‘b’, and ‘c’.|  

## Metadata Retrieval and Node IDs  
 The following table summarizes the metadata characteristics returned by [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

|Artifact|Metadata Characteristics|  
|--------------|------------------------------|  
|Table or View|<ul><li>Table name.</li><li>Table field names.</li><li>Table field data types are mapped to simple or complex WSDL types.</li><li>Table field length is mapped to facet maxLength.</li><li>Table field primary key constraint is mapped to facet minOccurs = 1.</li><li>Table field NULL constraint is mapped to facet isNillable = true.</li><li>Table operations<br /><br /> <ul><li>INSERT</li><li>SELECT</li><li>UPDATE</li><li>DELETE</li><li>SET\<Column Name\></li></ul></li></ul>|  
|Procedure or Function|-   Procedure or function name is mapped to the operation name.<br />-   Procedure or function parameter names.<br />-   Procedure or function parameter data types are mapped to WSDL types.<br />-   Procedure or function parameter direction is mapped to WSDL parameter direction.<br />-   Procedure parameter or function parameter data type length is mapped to facet maxLength.<br />-   Procedure or function parameter order is mapped to element sequence.<br />-   Function return data type is mapped to WSDL type.<br />-   Function return data type length is mapped to facet maxLength.|  

 For detailed information about the format of the metadata that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes for specific artifacts and operations on the SQL Server database, see [Messages and Message Schemas for BizTalk Adapter for SQL Server](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).  
