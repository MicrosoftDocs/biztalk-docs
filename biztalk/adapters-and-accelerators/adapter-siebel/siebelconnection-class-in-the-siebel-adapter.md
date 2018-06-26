---
title: "SiebelConnection class in the Siebel adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Data Provider for Siebel, SiebelConnection"
  - "SiebelConnection, supported properties and methods"
  - "SiebelConnection"
ms.assetid: 661d9876-4c14-4748-b05f-cc4fd1c4ebcf
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SiebelConnection class in the Siebel adapter
The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] accesses the underlying [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]`Binding`, the `ConnectionFactory`, and `Channel` to connect to the Siebel system. The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] implements the `DbConnection` class to support the preceding features.  

 Using an instance of `Microsoft.Data.SiebelClient.SiebelClientFactory`, a client program can obtain an instance of the `System.Data.Common.DbConnection` class to connect to the Siebel system.  

```  
//In this example, factory is an instance of SiebelClientFactory  
DbConnection connection = factory.CreateConnection();  
```  

 Alternatively, the following approach can be used to create a connection:  

```  

SiebelConnection connection = new SiebelConnection();  
connection.ConnectionString = connectionString;  
```  

 The `SiebelConnection` class inherits from `DbConnection`. It exists in the namespace `Microsoft.Data.SiebelClient`.  

## Supported Properties  
 The `SiebelConnection` class supports the following `DbConnection` properties.  


|         Name         |   Get/Set   |                                                                                                      Description                                                                                                       |
|----------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **ConnectionString** | Get and Set |                                                                                  Gets or sets the string used to open the connection.                                                                                  |
|     **Database**     |     Get     |        Gets the name of the current database after a connection is opened, or the database name specified in the connection string before the connection is opened. This should be the Siebel repository name.         |
|    **DataSource**    |     Get     |                                                                                Gets the name of the Siebel gateway for this connection.                                                                                |
|  **ServerVersion**   |     Get     | In the current version of [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], this property returns a hard-coded value, which does not represent the actual version of the Siebel server. |
|      **State**       |     Get     |                                               Gets a string that describes the state of the connection. This can contain three possible values: OPEN, BROKEN, or CLOSED.                                               |

## Supported Methods  
 The `SiebelConnection` class supports the following `DbConnection` methods.  

|Name|Description|  
|----------|-----------------|  
|**CreateDbCommand**|This protected method provides a new DbCommand instance.|  
|**ChangeDatabase**|This public method is not supported, and will throw an exception if called.|  
|**Open**|Opens a connection with the Siebel system by creating a WCF channel.|  
|**Close**|Closes a connection with the Siebel system by closing a WCF channel.|  
|**CreateCommand**|Creates a command object.|  

## See Also  
 [Extend ADO.NET Interfaces with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)