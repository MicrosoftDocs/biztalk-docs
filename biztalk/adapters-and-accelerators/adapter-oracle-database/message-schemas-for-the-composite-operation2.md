---
title: "Message Schemas for the Composite Operation2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0164ea07-a373-430b-b569-3e29df1d081b
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for the Composite Operation
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] enables you to execute composite operations on the Oracle database. A composite operation can contain multiple operations, and in any order. For information about which operations can be included in a composite operation, see [Run Composite Operations in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md).  
  
 For information about how to perform composite operations using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).  
  
## Message Structure for the Composite Operation  
 Because a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations. The composite operation message follows a request-response message exchange pattern.  
  
 The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a packaged stored procedure that does not take any input parameters, and a Delete operation.  
  
|Operation|XML Message|  
|---------------|-----------------|  
|Composite Operation Request|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <RECORDSET>       <[TABLE_NAME]RECORDINSERT>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>         …       </[TABLE_NAME]RECORDINSERT>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="[VERSION]/[SCHEMA]/Procedure" />   <Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|Composite Operation Response|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="[VERSION]/[SCHEMA]/Procedure">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 [VERSION] = The message version string; for example, http://Microsoft.LobServices.OracleDB/2007/03  
  
 [PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.  
  
 [COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [TABLE_NAME] = Name of the table; for example, EMPLOYEE.  
  
 [FIELD1_NAME] = Table field name; for example, NAME.  
  
 [SP_NAME] = The packaged stored procedure to be executed; for example, ADD_EMP_DETAILS.  
  
 [PRM1_NAME] = The name of the Oracle parameter in the stored procedure.  
  
## Message Action for the Composite Operation  
 The message action for the composite operation is “<http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation.”>  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)