---
title: "Message Schemas for Special LOB Operations2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "LOB data types, message structure of"
  - "LOB data types, message actions for"
ms.assetid: 031989d5-3209-41ab-8836-a40539781e74
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for Special LOB Operations
The ReadLOB and UpdateLOB operations are surfaced for tables and views that contain LOB columns; that is columns that are used to store Oracle large object (LOB) data. These operations enable you to read or write the LOB data as a stream of base64Binary-encoded data. They operate on a single column of LOB data in a single row.  

 For an overview of the ReadLOB and UpdateLOB operations and of the Oracle LOB data types supported, see [Operations on tables and views that contain LOB data in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md).  

## Message Structure of LOB Data-Type Operations  
 The following table shows the structure of the request and response messages for the ReadLOB and UpdateLOB operations. The target table for the operation is specified in the message action and also appears in the target namespace.  


|     Operation      |                                                                                    XML Message                                                                                     |                                                                                                                                                                                                                                                                                                                                Description                                                                                                                                                                                                                                                                                                                                 |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      ReadLOB       |                  `<ReadLOB xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   <LOB_COLUMN>[COL_NAME]</LOB_COLUMN>   <FILTER>[WHERE_clause]</LOB_COLUMN> </ReadLOB>`                  | The LOB data in the<br /><br /> - column identified by the LOB_COLUMN element, and the<br /><br /> - row that matches the where clause specified in the FILTER element<br /><br /> is returned.<br /><br /> The where clause should match only a single row. If there is more than one matching row, the LOB data in the first matching row is returned.<br /><br /> **Important** The ReadLOB operation is designed to support input streaming of LOB data in the WCF service model. You should use a table Select operation to read LOB data from a WCF Channel Model or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution. |
|  ReadLOB Response  |                      `<ReadLOBResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   <ReadLOBResult>     [LOB_DATA]   </ReadLOBResult> </ReadLOBResponse>`                      |                                                                                                                                                                                                                            The LOB data is returned as a stream of base64Binary encoded data.<br /><br /> **Important** The WSDL returned by the adapter does not match the actual schema used by the adapter for the ReadLOB response message.                                                                                                                                                                                                                            |
|     UpdateLOB      | `<UpdateLOB xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   <LOB_COLUMN>[COL_NAME]</LOB_COLUMN>   <FILTER>[WHERE_clause]</LOB_COLUMN>   <Stream>[LOB_DATA]</Stream> </UpdateLOB>` |                                                                                            The LOB data in the<br /><br /> - column identified by the LOB_COLUMN element, and the<br /><br /> - row that matches the where clause specified in the FILTER element<br /><br /> is updated with the base64Binary encoded data in the stream.<br /><br /> The where clause should match only a single row. If there is more than one matching row, an exception is thrown.<br /><br /> **Note** The UpdateLOB operation replaces all of the data in the specified column and row.                                                                                             |
| UpdateLOB Response |                                              `<UpdateLOBResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]"> </UpdateLOBResponse>`                                              |                                                                                                                                                                                                                                                                                                                       An empty response is returned.                                                                                                                                                                                                                                                                                                                       |

 [VERSION] = The message version string; for example, "<http://Microsoft.LobServices/OracleDB/2007/03>".  

 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  

 [TABLE_NAME] = The table that contains the targeted LOB column; for example, EMP.  

 [COL_NAME] = The name of the targeted LOB column; for example, LOB_FIELD.  

 [WHERE_clause] = An Oracle database SELECT statement WHERE clause that matches a single row; for example, ID = 1.  

 [LOB_DATA] = The LOB column data in base64Binary type.  

> [!IMPORTANT]
>  The message structure for the ReadLOB and UpdateLOB operations on views is the same as that on tables except that the namespace for the operation specifies a view rather than a table: `<ReadLOB xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`.  

## Message Actions for LOB Data-Type Operations  
 The following table shows the message actions that are used by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for the ReadLOB and UpdateLOB operations on tables. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the table name specified in the message action to determine the target table for the operation.  

|Operation|Action|Example|  
|---------------|------------|-------------|  
|ReadLOB|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/ReadLOB`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/ReadLOB`|  
|ReadLOB Response|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/ReadLOB/response`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/ReadLOB/response`|  
|UpdateLOB|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/UpdateLOB`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB`|  
|UpdateLOB Response|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/UpdateLOB/response`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB/response`|  

 [VERSION] = The message version string; for example, "<http://Microsoft.LobServices.OracleDB/2007/03>".  

 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  

 [TABLE_NAME] = The table that contains the targeted LOB column; for example, CUSTOMER. (The SCOTT.CUSTOMER table is installed by a SQL script included in the samples.)  

> [!IMPORTANT]
>  The message action for ReadLOB and UpdateLOB operations on views is similar to that used for tables, except that action for the operation specifies a view rather than a table: `[VERSION]/[SCHEMA]/View/[VIEW_NAME]/ReadLOB`.  

## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)