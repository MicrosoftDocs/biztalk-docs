---
title: "Managed Provider for DB22 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0dbd47b6-0b63-4126-8b57-331d0de4eedf
caps.latest.revision: 3
---
# Managed Provider for DB2
[!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] includes a Managed Provider to access data from a loosely coupled data source: in this case, a DB2 database. The Managed Provider for DB2 uses two central .NET Framework components to implement this capability: the ADO.NET `DataSet` object and the Managed Provider for DB2 itself.  
  
 A `DataSet` object is designed for data access independent of any data source. As a result, it can be used with multiple and different data sources, with XML data, or to manage data local to the application. A `DataSet` contains a collection of one or more `DataTable` objects consisting of rows and columns of data, and also primary key, foreign key, constraint, and relation information about the data in the `DataTable` objects.  
  
 In contrast, the Managed Provider for DB2 provides data manipulation and fast, forward-only, read-only access to data. Therefore, the Managed Provider for DB2 exposes a specific set of objects. The MSDb2Command object enables access to DB2 commands to return data, modify data, run stored procedures, and send or retrieve parameter information. The MsDb2DataReader provides a high-performance stream of data from the DB2 database. Finally, the MsDb2DataAdapter provides the bridge between the `DataSet` object and the DB2 database. MsDb2DataAdapter uses MsDb2Command objects to execute SQL commands at the data source to both load the `DataSet` with data, and reconcile changes that were made to the data in the `DataSet` back to the data source.  
  
## In This Section  
 [Managed Provider for DB2 Goals](../core/managed-provider-for-db2-goals2.md)  
  
 [Relationships between the .NET Provider for DB2 Interfaces](../core/relationships-between-the-net-provider-for-db2-interfaces1.md)