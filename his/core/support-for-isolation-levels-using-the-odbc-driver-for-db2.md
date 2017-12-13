---
title: "Support for Isolation Levels Using the ODBC Driver for DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f56fed1d-d603-4dfa-9e33-ef96a4da8964
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Support for Isolation Levels Using the ODBC Driver for DB2
The Microsoft ODBC Driver for DB2 provides flexibility in dealing with issues of isolation levels and transaction state. The ODBC **SQLSetConnectAttr** function is used to set the isolation level that is to be used for a connection. This function would be called with the attribute parameter set to SQL_ATTR_TXN_ISOLATION and the *ValuePtr* parameter pointing to an integer value indicating the isolation level requested. This integer value is a 32-bit bitmask that sets the transaction isolation level for the current connection.  
  
 The allowable values for isolation level (the *ValuePtr* parameter when calling **SQLSetConnectAttr**) can be determined by calling **SQLGetInfo** with InfoType equal to SQL_TXN_ISOLATION_OPTION. The following table list the allowable values for isolation level using the ODBC Driver for DB2 supplied with Host Integration Server.  
  
|ODBC Isolation Level Attribute|Description|  
|------------------------------------|-----------------|  
|SQL_TXN_READ_COMMITTED|When this attribute value is set, it isolates any data read from changes by others and changes made by others by others cannot be seen. The re-execution of the read statement is affected by others. This does not support a repeatable read.<br /><br /> This is the default value for isolation level<br /><br /> This isolation level is also called Cursor Stability (CS) in IBM DB2 documentation.|  
|SQL_TXN_READ_UNCOMMITTED|When this attribute value is set, it does not isolate data read from changes by others and changes made by others by others can be seen. The re-execution of the read statement is affected by others. This does not support a repeatable read.<br /><br /> This isolation level is called Uncommitted Read (UR) in IBM DB2 documentation.|  
|SQL_TXN_REPEATABLE_READ|When this attribute value is set, it isolates any data read from changes by others and changes made by others cannot be seen. The re-execution of the read statement is affected by others. This supports a repeatable read.<br /><br /> This isolation level is called Read Stability (RS) in IBM DB2 documentation.|  
|SQL_TXN_SERIALIZABLE|When this attribute value is set, it isolates any data read from changes by others and changes made by others by others cannot be seen. The re-execution of the read statement is not affected by others. This supports a repeatable read.<br /><br /> This isolation level is called Repeatable Read (RR) in IBM DB2 documentation.|  
  
 The SQL_ATTR_TXN_ISOLATION attribute can be set only if there are no open transactions on the connection. An application must call **SQLEndTran** to commit or roll back all open transactions on a connection, before calling **SQLSetConnectAttr** with this option.  
  
 Some connection attributes support substitution of a similar value if the data source does not support the value specified in *ValuePtr*. In such cases, the driver returns SQL_SUCCESS_WITH_INFO and SQLSTATE 01S02 (Option value changed). To determine the substituted value, an application calls **SQLGetConnectAttr**.