---
title: "Command Object (OLE DB Provider for DB2)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20fe7649-0b05-43c3-b78f-ff4f95f82338
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Command Object (OLE DB Provider for DB2)
The **Command** object is created by an OLE DB consumer, or by a service provider on behalf of a consumer. A **Command** object is used to execute a distributed relational database architecture (DRDA)-specific command on a remote DB2 database server operating as a DRDA application server. The **Command** object supports executing Structured Query Language (SQL) commands when connected to remove DRDA application servers.  
  
 Commands are used for data definition, such as creating a table or granting privileges, and data manipulation, such as updating or deleting rows. A special case of data manipulation using the **Command** object is the creation of rowsets based on DB2 tables. When using the command text with DB2 database servers, table names specified in a command are by default passed as uppercase. If a table name uses mixed case, the table name must be passed in a quoted string.  
  
 Before a consumer can use a command, it must determine if commands are supported. To do this, the consumer calls **QueryInterface** for **IDBCreateCommand** on a session. If this interface is exposed, the provider supports commands. To create a command, the consumer then calls **IDBCreateCommand::CreateCommand** on the session. A single session can be used to create multiple commands.  
  
 When the command is first created, it does not contain a command text. The consumer sets the command text with **ICommandText::SetCommandText**. Because the text command syntax is provider-specific, the consumer passes the globally unique identifier (GUID) of the syntax to use. For use with Microsoft OLE DB Provider for DB2, the GUID is DBGUID_DBSQL. Note that under OLE DB Provider for DB2, this GUID signifies that the text command is a subset of ANSI SQL. The level at which the provider supports ANSI SQL is specified by the DBPROP_SQLSUPPORT property. This property is a bitmask specifying the level of support for SQL.  
  
 The syntax supported by OLE DB Provider for DB2 for command text is as Entry-Level ANSI SQL 92 (with some exceptions based on the DB2 server platform and version).  
  
 Valid SQL commands are documented in the following publications published by IBM:  
  
- *DB2 for z/OS SQL Reference Version 9*  
  
- *DB2 for z/OS  SQL Reference Version 8*  
  
- *DB2 for i5/OS SQL Reference Version 6 Release 1*  
  
- *DB2 for i5/OS SQL Reference Version 5 Release 4*  
  
- *DB2 for LUW SQL Reference Version 9*  
  
  To execute the command, the consumer calls **ICommand::Execute**. If the command text specifies the command to open a rowset, **Execute** instantiates the rowset and returns an interface pointer to it.  
  
  The following interfaces of the **Command** object are supported by the current version of OLE DB Provider for DB2:  
  
- **IAccessor**  
  
- **IColumnsInfo**  
  
- **ICommand**  
  
- **ICommandPrepare**  
  
- **ICommandProperties**  
  
- **ICommandText**  
  
- **ICommandWithParameters**  
  
- **IConvertType**  
  
- **ISupportErrorInfo**  
  
  When using the **ICommand** object, Microsoft OLE DB Provider for DB2 may not derive parameter type information from the data store, depending on the DB2 platform and version. The OLE DB client application can supply the native parameter type information through **ICommandWithParameters::SetParameterInfo** function. The OLE DB provider uses the type information specified by **SetParameterInfo** to determine how to convert parameter data from the type supplied by the consumer (as indicated by the wType value in the binding structure) to the native type used by the data store. When the consumer specifies a data type with known precision, scale, and size values, any information supplied by the consumer for precision, scale, or size is ignored by OLE DB Provider for DB2.  
  
  The information that the consumer supplies should be correct and should be supplied for all parameters. OLE DB Provider for DB2 may verify the supplied information against the parameter metadata, depending on the DB2 platform and version, although the OLE DB provider will always determine that the specified values are legal values for the provider. The information that the consumer supplies must be correct and must be supplied for all parameters. OLE DB Provider for DB2 cannot verify the supplied information against the parameter metadata, although the OLE DB provider can determine that the specified values are legal values for the provider. The result of executing a command using incorrect parameter information or passing parameter information for the wrong number of parameters is undefined. For example, if the parameter type is **LONG** and the consumer specifies a type indicator of DBTYPE_STR in **ICommandWithParameters::SetParameterInfo**, OLE DB Provider for DB2 converts the data to a string before sending it to the data store. Because the data store is not expecting a **LONG**, this will likely result in an error.