---
title: "SiebelCommand class in the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SiebelCommand"
  - "Data Provider for Siebel, SiebelCommand"
  - "SiebelCommand, supported methods and properties"
ms.assetid: 7cba0e47-634b-4878-b480-80fbcbbf5c90
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SiebelCommand class in the Siebel adapter
After establishing a connection with the Siebel system, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] parses the Siebel command strings and command parameters provided by the ADO.NET client and maps the command into a WCF request message. The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] then sends the request to the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and obtains the response XML and the body contents from the adapter. The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] then uses the `XMLDataReader` to retrieve the relational data from the XML body.  
  
 Using an instance of `Microsoft.Data.SiebelClient.SiebelClientFactory`, a client program can obtain an instance of the `System.Data.Common.DbCommand` class to construct a Siebel command.  
  
```  
//In this example, factory is an instance of SiebelClientFactory  
DbCommand command = factory.CreateCommand();  
```  
  
 Alternatively, the following approach can be used to create a command:  
  
```  
//Here connection is an instance of SiebelConnection  
SiebelCommand cmd = (SiebelCommand) connection.CreateCommand();  
cmd.CommandText = "SELECT [Name] as MyName, [City], [Country]  from Account.Account WHERE Name LIKE '3Com*' OPTION 'ViewMode 1'";  
```  
  
 The `SiebelCommand` class inherits from `DbCommand`.  It exists in the namespace `Microsoft.Data.SiebelClient`.  
  
## Supported Properties  
 The **SiebelCommand** class supports the following `DbCommand`*protected* properties:  
  
|Name|Get/Set|Description|  
|----------|--------------|-----------------|  
|**DbConnection**|Get and Set|This should contain the underlying `DbConnection` instance from which this `DbCommand` instance is obtained.|  
|**DbParameterCollection**|Get|Gets the collection of `DbParameter` objects.|  
  
 `SiebelCommand` also supports the following `DbCommand`*public* properties:  
  
|Name|Get/Set|Description|  
|----------|--------------|-----------------|  
|**CommandText**|Get and Set|This contain the SQL statement that the ADO.NET client wishes to execute.|  
|**CommandType**|Get and Set|Only `CommandType.Text` is supported.|  
|**Connection**|Get and Set|This uses the `DbConnection` member.|  
|**Parameters**|Get|This uses the `DbParameterCollection` member.|  
  
> [!IMPORTANT]
>  The `SiebelCommand` class ignores the `CommandTimeout`, `DesignTimeVisible`, and `DbTransaction` properties.  
  
## Supported Methods  
 The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports the following `DbCommand`*protected* methods:  
  
|Name|Description|  
|----------|-----------------|  
|**CreateDbParameter**|Creates a new `DbParameter` instance.|  
|**ExecuteDbDataReader**|This executes the SELECT and EXEC commands and returns a `DbDataReader`.|  
  
 `SiebelCommand` also supports the following `DbCommand`*public* methods:  
  
|Name|Description|  
|----------|-----------------|  
|**CreateParameter**|Creates a new `DbParameter` instance through `CreateDbParameter().`|  
|**ExecuteReader**|Executes `CommandText` against the `Connection` and returns `DbDataReader` through `ExecuteDbDataReader()`.|  
|**Prepare**|This parses the `CommandText` and builds the SQL command parse tree.|  
  
## See Also  
 [Extend ADO.NET Interfaces with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)