---
title: "Message Schemas for RECORD Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RECORD types, message schemas for"
  - "RECORD types, support for"
ms.assetid: 637c42f2-eed0-4941-a6cd-7e03d01088b8
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for RECORD Types
Oracle RECORD types are structured PL/SQL data types that consist of one or more simple or structured database types. RECORD types are primarily used in PL/SQL stored procedures and functions to send and receive hierarchical data.  
  
 The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports RECORD types in the following manner:  
  
- RECORD types are surfaced as complex types.  
  
- RECORD types can be nested (record in a record).  
  
- RECORD types can be declared as TABLE%ROWTYPE parameters in stored procedures and functions.  
  
- RECORD types can be declared as TYPE of RECORD parameters in PL/SQL packages; for example, `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`.  
  
  > [!NOTE]
  >  The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support BFILE types as RECORD members.  
  
  When a RECORD type parameter is used in a stored procedure or a function, it is qualified with the namespace of that operation. The following XML shows the structure of a RECORD type in a message:  
  
```  
<[REC_PARAM_NAME]>  
  <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
  <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value2</[FIELD_NAME2]>  
  …  
</[REC_PARAM_NAME]>  
```  
  
 [REC_PARAM_NAME] is the name of the RECORD parameter.  
  
 [FIELD_NAME] is the name of a field in the RECORD type.  
  
 [OPERATION_NAMESPACE] is the namespace of the stored procedure or function in which the RECORD parameter is being used.  
  
 The following XML shows the structure of a RECORD type parameter with a nested RECORD type field:  
  
```  
<[REC_PARAM_NAME]>    
  <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
  <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value2</[FIELD_NAME2]>  
  <[REC_PARAM_NAME2]>  
    <[FIELD_NAME1] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME1]>  
    <[FIELD_NAME2] xmlns="[OPERATION_NAMESPACE]">value1</[FIELD_NAME2]>  
    …  
  </[REC_PARAM_NAME2]>  
  …  
</[REC_PARAM_NAME]>  
```  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)