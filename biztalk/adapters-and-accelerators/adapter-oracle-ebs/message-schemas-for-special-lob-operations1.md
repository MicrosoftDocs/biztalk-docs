---
title: "Message Schemas for Special LOB Operations1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2e418a6-8bc7-42d9-9672-a9c149f32778
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for Special LOB Operations
The Read_\<LOBColName\> and Update_\<LOBColName\> operations are surfaced for tables and views that contain LOB columns, where \<LOBColName\> is the LOB column in the table or view. These operations enable you to read or write the LOB data as a stream of base64Binary-encoded data. They operate on a single column of LOB data in a single row.  
  
 For an overview of the Read_\<LOBColName\> and Update_\<LOBColName\> operations and of the Oracle LOB data types supported, see [Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).  
  
## Message Structure of LOB Data-Type Operations  
 The following table shows the structure of the request and response messages for the Read_\<LOBColName\> and Update_\<LOBColName\> operations. The target table for the operation is specified in the message action and also appears in the target namespace.  
  
> [!NOTE]
>  See entity descriptions after the table.  
  
|           Operation            |                                                                                  XML Message                                                                                  |                                                                                                                                                                                                                                                              Description                                                                                                                                                                                                                                                              |
|--------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Read_\<LOBColName\>       |                           `<Read_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</FILTER></Read_[LOBColName]>`                           |                                                                                                           The LOB data in the row that matches the where clause specified in the FILTER element is returned. The where clause should match only a single row. If there is more than one matching row, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] will throw an exception.                                                                                                            |
|  Read_\<LOBColName\> Response  | `<Read_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <Read_[LOBColName]Result>    [LOB_DATA]  </Read_[LOBColName]Result></Read_[LOBColName]Response>` |                                                                                                                                                                                                                                  The LOB data is returned as a stream of base64Binary encoded data.                                                                                                                                                                                                                                   |
|     Update_\<LOBColName\>      |            `<Update_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</LOB_COLUMN>  <DATA>[Value]</DATA></Update_[LOBColName]>`            | The LOB data in the row that matches the where clause specified in the FILTER element is updated with the data in the \<DATA\> element. The where clause should match only a single row. If there is more than one matching row, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] throws an exception.<br /><br /> **Note** While updating BLOB columns, the \<DATA\> element must always contain a base64 encoded value. For CLOB and NCLOB, the \<DATA\> element can have string values. |
| Update_\<LOBColName\> Response |                                 `<Update_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]"></Update_[LOBColName]Response>`                                  |                                                                                                                                                                                                                                                    An empty response is returned.                                                                                                                                                                                                                                                     |
  
 Entity descriptions:  
  
 [VERSION] = The message version string; for example, "<http://schemas.microsoft.com/OracleEBS/2008/05>".  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [TABLE_NAME] = The table that contains the targeted LOB column; for example, CUSTOMER.  
  
 [LOBCol_Name] = The name of a LOB column; for example, Photo.  
  
 [WHERE_clause] = An Oracle database SELECT statement WHERE clause that matches a single row; for example, ID = 1.  
  
 [LOB_DATA] = The LOB column data in base64Binary type.  
  
> [!IMPORTANT]
>  The message structure for the Read_\<LOBColName\> and Update_\<LOBColName\> operations on views is the same as that on tables except that the namespace for the operation specifies a view rather than a table: `<ReadLOB xmlns ="[VERSION]/Views/[SCHEMA]/[VIEW_NAME]">`.  
  
## Message Actions for LOB Data-Type Operations  
 The following table shows the message actions that are used by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] for the Read_\<LOBColName\> and Update_\<LOBColName\> operations on tables. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the table name and the LOB column name specified in the message action to determine the target table and LOB column for the operation.  
  
> [!NOTE]
>  See entity descriptions after the table.  
  
|Operation|Action|Example|  
|---------------|------------|-------------|  
|Read_\<LOBColName\>|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo`|  
|Read_\<LOBColName\> Response|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo/response`|  
|Update_\<LOBColName\>|**For BLOB**:<br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`<br /><br /> **For CLOB and NCLOB**:<br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|**For BLOB**:<br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/`<br /><br /> **For CLOB and NCLOB**:<br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/`|  
|Update_\<LOBColName\> Response|**For BLOB**:<br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`<br /><br /> **For CLOB and NCLOB**:<br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|**For BLOB**:<br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/response`<br /><br /> **For CLOB and NCLOB**:<br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/response`|  
  
 Entity descriptions:  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [TABLE_NAME] = The table that contains the targeted LOB column; for example, CUSTOMER. (The SCOTT.CUSTOMER table is installed by a SQL script included in the samples.)  
  
 [LOBCol_Name] = The name of a LOB column; for example, Photo.  
  
> [!IMPORTANT]
>  The message action for Read_\<LOBColName\> and Update_\<LOBColName\> operations on views is similar to that used for tables, except that action for the operation specifies a view rather than a table: `Views/ReadLOB/[SCHEMA]/[VIEW_NAME]/[LOBColName]`.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)