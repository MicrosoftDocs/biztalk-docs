---
description: "Learn about the message schemas for composite operations used by the Microsoft BizTalk Adapter for Oracle E-Business Suite."
title: "Message Schemas for the Composite Operation1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 768473ef-da8d-4e58-86cb-597c28ded49c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for the Composite Operation

The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] enables you to execute composite operations in Oracle E-Business Suite. A composite operation can contain multiple operations, and in any order. For information about which operations can be included in a composite operation, see [Support for Composite Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).  
  
 For information about how to perform composite operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).  
  
## Message Structure for the Composite Operation  

Since a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations. The composite operation message follows a request-response message exchange pattern.  
  
The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a packaged stored procedure that does not take any input parameters, and a Delete operation.  
  
> [!NOTE]
> See entity descriptions after the table.  
  
|Operation|XML Message|  
|---------------|-----------------|  
|Composite Operation Request|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <Recordset>       <InsertRecord>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>           <InLineValue>[value]</InlineValue>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>           <InLineValue>[value]</InlineValue>         …       <InsertRecord>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/[SCHEMA]/[APP_NAME]" />   <Delete xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|Composite Operation Response|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Procedures/[SCHEMA]">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 Entity descriptions:  
  
 [PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.  
  
 [COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [TABLE_NAME] = Name of the table; for example, EMPLOYEE.  
  
 [FIELD1_NAME] = Table field name; for example, NAME.  
  
 [SP_NAME] = The packaged stored procedure to be executed; for example, ADD_EMP_DETAILS.  
  
 [APP_NAME] = Name of the Oracle Application that contains the packaged stored procedure.  
  
 [PRM1_NAME] = The name of the Oracle parameter in the packaged stored procedure.  
  
## Message Action for the Composite Operation 
 
The message action for the composite operation is “CompositeOperation.”  
  
## See Also
  
[Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)
