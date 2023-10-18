---
description: "Learn more about: Message Schemas for Procedures and Functions"
title: "Message Schemas for Procedures and Functions"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Message Schemas for Procedures and Functions
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces SQL Server database stored procedures and scalar and table valued functions as operations. This section describes the message structure and actions used to invoke procedures and functions.  
  
## Message Structure of Procedures and Functions  
 The operations surfaced for procedures and functions follow a request-response message exchange pattern. The following table shows the structure of these request and response messages.  
  
|Operation|XML Message|Description|  
|---------------|-----------------|-----------------|  
|Stored Procedure Request|`<[SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[SP_NAME]>`|-|  
|Stored Procedure Response|`<[SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">   <[SP_NAME]Result>      <DataSet>        <any>[Value]</any>       <any>[Value]</any>       …     </DataSet>   </[SP_NAME]Result>   <ReturnValue>[Value]</ReturnValue> </[SP_NAME]Response>`|The return value of a stored procedure is an array of DataSet.|  
|Strongly-Typed Stored Procedure Request|`<[STRNG_SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/[SCHEMA]">   <[PRM1_NAME]>value1<[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[STRNG_SP_NAME]>`|-|  
|Strongly-Typed Stored Procedure Response|`<[STRNG_SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/[SCHEMA]">     <StoredProcedureResultSet0>          <StoredProcedureResultSet0 xmlns:ns1="http://schemas.microsoft.com/Sql/2008/05/ProcedureResultSets/[SCHEMA]/[STRNG_SP_NAME]">               <[PRM1_NAME]>value1<[PRM1_NAME]>               <[PRM2_NAME]>value2</[PRM2_NAME]>               …         </StoredProcedureResultSet0>     </StoredProcedureResultSet0>    <ReturnValue>[Value]</ReturnValue> </[STRNG_SP_NAME]Response>`|The return value of a strongly-typed stored procedure is an array of strongly-typed data.|  
|Scalar Function Request|`<[SCLR_FN_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/ScalarFunctions/[SCHEMA]">   <[PRM_NAME]>value</[PRM_NAME]> </[SCLR_FN_NAME]>`|-|  
|Scalar Function Response|`<[SCLR_FN_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/ScalarFunctions/[SCHEMA]">   <[SCLR_FN_NAME]Result>return_value</[SCLR_FN_NAME]Result>   <[PRM_NAME]>value</[PRM_NAME]>   </[SCLR_FN_NAME]Response>`|-|  
|Table Valued Function Request|`<[TBL_FN_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/[SCHEMA]">   <[PRM1_NAME]>value1</[PRM1_NAME]>   <[PRM2_NAME]>value2</[PRM2_NAME]>   … </[TBL_FN_NAME]>`|-|  
|Table Valued Function Response|`<[TBL_FN_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/[SCHEMA]">   <[TBL_FN_NAME]Result>      <[TBL_FN_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/[SCHEMA]">         <[PRM1_NAME]>value1</[PRM1_NAME]>         <[PRM2_NAME]>value2</[PRM2_NAME]>         ...      </[TBL_FN_NAME]">        ...      </[TBL_FN_NAME]Result> </[TBL_FN_NAME]Response>`||  
  
 [SCHEMA] = Collection of SQL Server artifacts; for example, dbo.  
  
 [SP_NAME] = The stored procedure to be executed; for example, ADD_EMP_DETAILS.  
  
 [STRNG_SP_NAME] = The strongly-typed stored procedure to be executed; for example, GET_EMP_DETAILS.  
  
 [SCLR_FN_NAME] = The scalar function to be executed; for example, GET_EMP_ID.  
  
 [TBL_FN_NAME] = The table valued function to be executed; for example, TVF_EMPLOYEE.  
  
 [PRM_NAME] = The name of the SQL Server parameter.  
  
## Message Actions of Functions and Procedures  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses the following message actions for stored procedure and function operations.  
  
|Message|Action|Example|  
|-------------|------------|-------------|  
|Stored Procedure Request|Procedure/[SCHEMA]/[SP_NAME]|Procedure/dbo/ADD_EMP_DETAILS|  
|Stored Procedure Response|Procedure/[SCHEMA]/[SP_NAME]/response|Procedure/dbo/ADD_EMP_DETAILS/response|  
|Strongly-Typed Stored Procedure Request|TypedProcedure/[SCHEMA]/[STRNG_SP_NAME]|TypedProcedure/dbo/GET_EMP_DETAILS|  
|Strongly-Typed Stored Procedure Response|TypedProcedure/[SCHEMA]/[STRNG_SP_NAME]/response|TypedProcedure/dbo/GET_EMP_DETAILS/response|  
|FOR XML Stored Procedure Request|XmlProcedure/[SCHEMA]/[SP_NAME]|XmlProcedure/dbo/GET_EMP_DETAILS_FOR_XML|  
|FOR XML Stored Procedure Response|XmlProcedure/[SCHEMA]/[SP_NAME]/resp|XmlProcedure/dbo/GET_EMP_DETAILS_FOR_XML/response|  
|Scalar Function Request|ScalarFunction/[SCHEMA]/[SCLR_FN_NAME]|ScalarFunction/dbo/GET_EMP_ID|  
|Scalar Function Response|ScalarFunction/[SCHEMA]/[SCLR_FN_NAME]/response|ScalarFunction/dbo/GET_EMP_ID/response|  
|Table Valued Function Request|TableFunction/[SCHEMA]/[TBL_FN_NAME]|TableFunction/dbo/TVF_EMPLOYEE|  
|Table Valued Function Response|TableFunction/[SCHEMA]/[TBL_FN_NAME]/response|TableFunction/dbo/TVF_EMPLOYEE/response|  
  
 [SP_NAME] = The stored procedure to be executed; for example, ADD_EMP_DETAILS.  
  
 [STRNG_SP_NAME] = The strongly-typed stored procedure to be executed; for example, GET_EMP_DETAILS.  
  
 [SCLR_FN_NAME] = The scalar function to be executed; for example, GET_EMP_ID.  
  
 [TBL_FN_NAME] = The name of the table valued function to be executed; for example, TVF_EMPLOYEE.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)
