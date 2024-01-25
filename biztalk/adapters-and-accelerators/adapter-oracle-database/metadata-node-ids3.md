---
title: "Metadata Node IDs for the Oracle DB adapter in BizTalk Adapter Pack"
description: Metadata, search, retrieval nodes types and IDs used in Oracle components that are exposed in Oracle DB adapter - BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Node types and IDs for the Oracle Database adapter

## Metadata node types and IDs 
The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces Oracle database artifacts in a hierarchical manner. The following table lists the node types and node IDs for Oracle database artifacts that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces. The node ID is the absolute path of the node that is used in the **IMetadataRetrievalContractBrowse**, **Search**, and **GetMetadata** methods.  

**Artifact Display Name: --**  
Node Type: CATEGORY  
Node ID: /  
Example: /  
Description: [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] root node. Returns all first-level nodes; this includes the SQLEXECUTE operation node, the POLLINGSTMT operation node, and all schema nodes

**Artifact Display Name: SQLEXECUTE**  
Node Type: OPERATION  
Node ID: [VERSION]/SQLEXECUTE  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE`  
Description: SQLEXECUTE operation node. Returns WSDL for the SQLEXECUTE operation.

**Artifact Display Name: POLLINGSTMT**  
Node Type: OPERATION  
Node ID: [VERSION]/POLLINGSTMT  
Example: `http://Microsoft.LobServices. OracleDB/2007/03/POLLINGSTMT`  
Description: POLLINGSTMT operation node. Returns WSDL for the POLLINGSTMT operation.

**Artifact Display Name: [DB_SCHEMA]**  
Node Type: CATEGORY  
Node ID: [VERSION]/[DB_SCHEMA]  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT`  
Description: Schema node. Returns general category nodes (Table, View, Procedure, Function, and Package) for the specified schema.

**Artifact Display Name: Table**  
Node Type: CATEGORY  
Node ID: [VERSION]/[DB_SCHEMA]/Table  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table`  
Description: Schema tables node. Returns all table nodes for the specified schema.

**Artifact Display Name: [DB_TABLE]**  
Node Type: CATEGORY  
Node ID: [VERSION]/[DB_SCHEMA]/Table/[DB_TABLE]  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP`  
Description: Table node. Returns all operation nodes (Insert, Select, Update, Delete, ReadLOB, and UpdateLOB) for the specified table. (ReadLOB and UpdateLOB are only returned for tables that contain a LOB column.)

**Artifact Display Name: Insert**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Table/[DB_TABLE]/Insert  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert`  
Description: Table Insert operation node. Returns WSDL for the Insert operation for the specified table.

**Artifact Display Name: Select**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Table/[DB_TABLE]/Select  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select`  
Description: Table Select operation node. Returns WSDL for the Select operation for the specified table.

**Artifact Display Name: Update**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Table/[DB_TABLE]/Update  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update`  
Description: Table Update operation node. Returns WSDL for the Update operation for the specified table.

**Artifact Display Name: Delete**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Table/[DB_TABLE]/Delete  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete`  
Description: Table Delete operation node. Returns WSDL for the Delete operation for the specified table.

**Artifact Display Name: ReadLOB**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Table/[DB_TABLE]/ReadLOB  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/ReadLOB`  
Description: Table ReadLOB operation node. Returns WSDL for the ReadLOB operation for the specified table. (Only surfaced if the table contains a LOB column.)

**Artifact Display Name: UpdateLOB**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Table/[DB_TABLE]/UpdateLOB  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/UpdateLOB`  
Description: Table UpdateLOB operation node. Returns WSDL for the UpdateLOB operation for the specified table. (Only surfaced if the table contains a LOB column.)

**Artifact Display Name: View**  
Node Type: CATEGORY  
Node ID: [VERSION]/[DB_SCHEMA]/View  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View`  
Description: Schema views node. Returns all view nodes for the specified schema.

**Artifact Display Name: [DB_VIEW]**  
Node Type: CATEGORY  
Node ID: [VERSION]/[DB_SCHEMA]/View/[DB_VIEW]  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW`  
Description: View node. Returns all operation nodes (Insert, Select, Update, Delete, ReadLOB, and UpdateLOB) for the specified view. (ReadLOB and UpdateLOB are only returned for views that contain a LOB column.)

**Artifact Display Name: Insert**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/View/[DB_VIEW]/Insert  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/Insert`  
Description: View Insert operation node. Returns WSDL for the Insert operation for the specified view.

**Artifact Display Name: Select**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/View/[DB_VIEW]/Select  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/Select`  
Description: View Select operation node. Returns WSDL for the Select operation for the specified view.

**Artifact Display Name: Update**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/View/[DB_VIEW]/Update  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/Update`  
Description: View Update operation node. Returns WSDL for the Update operation for the specified view.

**Artifact Display Name: Delete**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/View/[DB_VIEW]/Delete  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/Delete`  
Description: View Delete operation node. Returns WSDL for the Delete operation for the specified view.

**Artifact Display Name: ReadLOB**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/View/[DB_VIEW]/ReadLOB  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/ReadLOB`  
Description: View ReadLOB operation node. Returns WSDL for the ReadLOB operation for the specified view. (Only surfaced if the view contains a LOB column.)

**Artifact Display Name: UpdateLOB**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/View/[DB_VIEW]/UpdateLOB  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/View/SALES_VIEW/UpdateLOB`  
Description: View Update operation node. Returns WSDL for the UpdateLOB operation for the specified table. (Only surfaced if the view contains a LOB column.)

**Artifact Display Name: Procedure**  
Node Type: CATEGORY  
Node ID: [VERSION]/[DB_SCHEMA]/Procedure  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure`  
Description: Schema procedures node. Returns all procedures for the specified schema.

**Artifact Display Name: [DB_PROCEDURE]**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Procedure/[DB_PROCEDURE]  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Procedure/SP_GENREPORT`  
Description: Procedure node. Returns the WSDL for the specified procedure.

**Artifact Display Name: Function**  
Node Type: CATEGORY  
Node ID: [VERSION]/[DB_SCHEMA]/Function  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function`  
Description: Schema functions node. Returns all functions for the specified schema.

**Artifact Display Name: [DB_FUNCTION]**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Function/[DB_FUNCTION]  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Function/FN_GETUSERID`  
Description: Function node. Returns the WSDL for the specified function.

**Artifact Display Name: Package**  
Node Type: CATEGORY  
Node ID: [VERSION]/[DB_SCHEMA]/Package  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package`  
Description: Schema packages node. Returns all packages for the specified schema.

**Artifact Display Name: [DB_PACKAGE]**  
Node Type: CATEGORY  
Node ID: [VERSION]/[DB_SCHEMA]/Package/[DB_PACKAGE]  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG`  
Description: Package node. Returns all procedures and functions for the specified package.

**Artifact Display Name: [PACK_PROCEDURE]**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Package/[DB_PACKAGE]/[PACK_PROCEDURE]  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT`  
Description: Package procedure node. Returns the WSDL for the specified package procedure.

**Artifact Display Name: [PACK_FUNCTION]**  
Node Type: OPERATION  
Node ID: [VERSION]/[DB_SCHEMA]/Package/[DB_PACKAGE]/[PACK_FUNCTION]  
Example: `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT`  
Description: Package function node. Returns the WSDL for the specified package function.

[VERSION] = The version string; for example, `http://Microsoft.LobServices.OracleDB/2007/03`.  

[DB_SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  

[DB_TABLE] = The name of an Oracle table; for example, EMP.  

[DB_VIEW] = The name of an Oracle view; for example, SALES_VIEW.  

[DB_PROCEDURE] = The name of an Oracle procedure; for example, SP_GENREPORT.  

[DB_FUNCTION] = The name of an Oracle function; for example, FN_GETUSERID.  

[DB_PACKAGE] = The name of an Oracle package; for example, ACCOUNT_PKG.  

[PACK_PROCEDURE] = The name of a package procedure; for example, GET_ACCOUNT.  

[PACK_FUNCTION] = The name of a package function; for example, CREATE_ACCOUNT.  

## Metadata Search and Node IDs  
 Metadata search is a powerful feature that the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] surfaces as part of its **MetadataRetrievalContract** interface. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses this feature to support searching on the following Oracle artifacts. The metadata search scope is restricted to the level immediately under the node at which the search operation is performed. For example, to search for a function, you must be searching under \\[Schema]\Functions. Recursive search is not supported.  

|Artifact|Node ID|Node Type Returned|Description|  
|--------------|-------------|------------------------|-----------------|  
|[DB_SCHEMA]|/ (i.e. Root node)|CATEGORY|Return all schema nodes that match the search expression.|  
|[DB_TABLE]|/[VERSION]/[DB_SCHEMA]/Table|CATEGORY|Return all table nodes in the specified schema that match the search expression.|  
|[DB_VIEW]|/[VERSION]/[DB_SCHEMA]/View|CATEGORY|Return all view nodes in the specified schema that match the search expression.|  
|[DB_PROCEDURE]|/[VERSION]/[DB_SCHEMA]/Procedure|OPERATION|Return all procedure nodes in the specified schema that match the search expression.|  
|[DB_FUNCTION]|/[VERSION]/[DB_SCHEMA]/Function|OPERATION|Return all function nodes in the specified schema that match the search expression.|  
|[DB_PACKAGE]|/[VERSION]/[DB_SCHEMA]/Package|CATEGORY|Return all package nodes (category) in the specified schema that match the search expression.|  
|[PACK_PROCEDURE] and [PACK_FUNCTION]|/[VERSION]/[DB_SCHEMA]/Package/[DB_PACKAGE]|OPERATION|Return all function and procedure nodes (operation) in the specified package that match the search expression.|  

 [VERSION] = The version string; for example, `http://Microsoft.LobServices/2007/03`.  

 [DB_SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  

 [DB_TABLE] = The name of an Oracle table; for example, EMP.  

 [DB_VIEW] = The name of an Oracle view; for example, SALES_VIEW.  

 [DB_PROCEDURE] = The name of an Oracle procedure; for example, SP_GENREPORT.  

 [DB_FUNCTION] = The name of an Oracle function; for example, FN_GETUSERID.  

 [DB_PACKAGE] = The name of an Oracle package; for example, ACCOUNT_PKG.  

 [PACK_PROCEDURE] = The name of a package procedure; for example, GET_ACCOUNT.  

 [PACK_FUNCTION] = The name of a package function; for example, CREATE_ACCOUNT.  

 You can specify search expressions that are compatible with any valid expression that can be used for the Oracle LIKE operator. For example, to perform a search on the tables contained in a schema, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes the following SQL: `SELECT TABLE_NAME FROM ALL_TABLES WHERE OWNER = '[OWNER_NAME]' AND TABLE_NAME LIKE ‘[SEARCH_STR]’`.  

 The following table lists the special characters that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports in search expressions.  

|Special Character|Interpretation|  
|-----------------------|--------------------|  
|% (percentage)|Matches zero or more characters; for example, "A%" matches "A", "AB", "ABC", and so on.|  
|_ (underscore)|Matches exactly 1 character; for example, "A_" matches "AB", "AC", "AD", and so on.|  
|\ (escape)|Escapes the special meaning of '%' and '_'; for example, "A\\_B" matches "A_B".|  

## Metadata Retrieval and Node IDs  
 The following table summarizes the metadata characteristics returned by [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  

|Artifact|Metadata Characteristics|  
|--------------|------------------------------|  
|Table or View|<ul><li>Table name.</li><li>Table field names.</li><li>Table field data types are mapped to simple or complex WSDL types.</li><li>Table field length is mapped to facet maxLength.</li><li>Table field primary key constraint is mapped to facet minOccurs = 1.</li><li>Table field NULL constraint is mapped to facet isNillable = true.</li><li>Table operations<br /><br /> <ul><li>INSERT</li><li>SELECT</li><li>UPDATE</li><li>DELETE</li><li>READLOB (if the table contains Oracle LOB type field)</li><li>UPDATELOB (if the table contains Oracle LOB type field)</li></ul></li></ul>|  
|Procedure or Function|-   Procedure or function name is mapped to the operation name.<br />-   Procedure or function parameter names.<br />-   Procedure or function parameter data types are mapped to WSDL types.<br />-   Procedure or function parameter direction is mapped to WSDL parameter direction.<br />-   Procedure parameter or function parameter data type length is mapped to facet maxLength.<br />-   Procedure or function parameter order is mapped to element sequence.<br />-   Function return data type is mapped to WSDL type.<br />-   Function return data type length is mapped to facet maxLength.|  
|Package Procedure or Function.|-   Package name.<br />-   Other procedure and function characteristics as listed above.|  

 For detailed information about the format of the metadata that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes for specific artifacts and operations on the Oracle database, see [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).  

## See Also  
[Get metadata for Oracle DB operations in Visual Studio](get-metadata-for-oracle-database-operations-in-visual-studio.md)
