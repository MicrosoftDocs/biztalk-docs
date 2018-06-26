---
title: "Message Schemas for REF CURSORS | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "REF CURSORS, message schemas for"
  - "IN REF CURSOR"
  - "OUT REF CURSOR"
  - "IN OUT REF CURSOR"
ms.assetid: b62e7a9f-278c-41b3-90f0-2f621a34327b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for REF CURSORS
A REF CURSOR is an Oracle PL/SQL data type that represents a pointer to a result set in the Oracle database. REF CURSOR types enable input and output streaming of data and are ideal for transferring large amounts of data to and from a PL/SQL code block. [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] provides support for passing strongly-typed and weakly-typed REF CURSOR parameters to PL/SQL procedures and functions as IN, OUT and IN OUT parameters.  
  
 In the Oracle database, a REF CURSOR type can be either strongly-typed or weakly-typed:  
  
- A strongly-typed REF CURSOR is declared with a RETURN clause as in `TYPE StrongCurType IS REF CURSOR RETURN emp%ROWTYPE;`. A strongly-typed REF CURSOR variable can only represent a result set that contains data that matches the type with which its REF CURSOR type is declared. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] returns a strongly-typed result set for a strongly-typed REF CURSOR.  
  
- A weakly-typed REF CURSOR is declared without a RETURN clause as in `TYPE WeakCurType IS REF CURSOR;`. Oracle also provides a special REF CURSOR type called SYS_REFCURSOR that can be used to declare weakly-typed REF CURSOR variables. Weakly-typed REF CURSOR variables can represent a result set that contains any kind of row data. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] returns a weakly-typed result set of generic records for a weakly-typed REF CURSOR.  
  
## IN REF CURSOR Parameters  
 There is no ODP.NET API to create a REF CURSOR on the Oracle server, so the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] cannot provide the capability for a client program to create and maintain REF CURSOR variables.  
  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does, however, enable a client to pass IN REF CURSOR parameters to functions or stored procedures by specifying a block of PL/SQL code that returns a REF CURSOR. The adapter uses this code to create and OPEN a REF CURSOR variable on the Oracle server; it then calls the function or stored procedure using this variable as the IN parameter.  
  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] represents IN REF CURSOR parameters as strings that contain the PL/SQL code block. Within this block, the location of the REF CURSOR is specified with a question mark (?). The PL/SQL code block can contain an OPEN-FOR statement that contains a SQL query; or it can contain a function or procedure call in which an opened REF CURSOR is returned in an OUT parameter.  
  
 The following shows how to specify an IN REF CURSOR by calling a stored procedure or function to open the REF CURSOR.  
  
```  
<[IN_REF_CURSOR_PARAM_NAME]>begin [SP_NAME]([SP_PARAMS...], ?, [SP_PARAMS...]); end;</[IN_REF_CURSOR_PARAM_NAME]>  
  
Example:  
<EMP_RC>begin GETEMP(1, ?); end; </EMP_RC>  
```  
  
 The following shows how to specify an IN REF CURSOR by using a SELECT query to open the REF CURSOR.  
  
```  
<IN_REF_CURSOR_PARAM_NAME>begin open ? for select [FIELD_NAMES] from [TABLE_NAME]; end;</IN_REF_CURSOR_PARAM_NAME>  
  
Example:  
<EMP_RC>begin open ? for select * from EMP; end;</EMP_RC>  
```  
  
## OUT REF CURSOR Parameters  
 OUT REF CURSOR parameters are returned as either strongly-typed or weakly-typed result sets. The type of the result set returned depends on whether the REF CURSOR parameter is declared as a strongly-typed or weakly-typed REF CURSOR in the stored procedure or function definition on the Oracle server. A strongly-typed result set is returned for strongly-typed REF CURSOR parameters and a weakly-typed result set is returned for weakly-typed REF CURSOR parameters (for example, parameters declared with a SYS_REFCURSOR type).  
  
 The following shows the XML for a strongly-typed OUT REF CURSOR parameter.  
  
```  
<[PARAM_NAME]>  
 <[PARAM_NAME]RECORD>  
  <[COL1_NAME]>value1</[COL1_NAME]>  
  <[COL2_NAME]>value2</[COL2_NAME]>  
  ...  
 </[PARAM_NAME]RECORD>  
</[PARAM_NAME]>  
  
[PARAM_NAME] = OUT REF CURSOR parameter name; for example, EMP_REFCURSOR  
[COL_NAME] = Name of a column in the REF CURSOR type; for example, Name.  
```  
  
 The following shows the XML for a weakly-typed OUT REF CURSOR parameter.  
  
```  
<[PARAM_NAME]>  
 <GenRecordRow xmlns="oracledb">  
  <GenRecordColumn>  
   <ColumnName>COL_NAME</ColumnName>  
   <ColumnValue>COL_VALUE</ColumnValue>  
   <ColumnType>COL_TYPE</ColumnType>  
  </GenRecordColumn>  
  …  
 </GenRecordRow>  
 …  
</[PARAM_NAME]>  
  
[COL_NAME] = Name of column; for example, Name  
[COL_VALUE] = Column value; for example, Scott  
[COL_TYPE] = Column data type; for example, System.String  
```  
  
## IN OUT REF CURSOR Parameters  
 Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] models IN REF CURSOR parameters as strings and OUT REF CURSOR parameters as complex types, it cannot support a single type for an IN OUT REF CURSOR parameter. For this reason, it treats IN OUT REF CURSOR parameters as two different parameters: an IN parameter in the request message and an OUT parameter in the response message.  
  
 To avoid a name conflict in service model programming, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] appends the string "_IN" to the IN parameter in the request message so that for a given parameter named [PARAM_NAME], two parameters are created:  
  
-   [PARAM_NAME]_IN is an IN REF CURSOR parameter in the stored procedure or function request message. It contains a PL/SQL statement (either a select query or a stored procedure or function call) that returns a REF CURSOR.  
  
-   [PARAM_NAME] is an OUT REF CURSOR parameter in the stored procedure or function response message. It contains the OUT REF CURSOR as a strongly-typed or weakly-typed result set.  
  
> [!IMPORTANT]
>  The adapter cannot support a procedure or function that contains an IN parameter named [PARAM_NAME]_IN and an IN OUT REF CURSOR parameter named [PARAM_NAME]. This is because the adapter expects a parameter named [PARAM_NAME]_IN to represent the input to the REF CURSOR parameter, and you cannot specify both parameters in the request message.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)