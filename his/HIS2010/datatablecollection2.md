---
title: "DataTableCollection2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3aadf3cf-f4a7-4a82-9b64-7fa3f5608ce2
caps.latest.revision: 3
---
# DataTableCollection
An ADO.NET `DataSet` contains a collection of zero or more tables represented by `DataTable` objects. The `DataTableCollection` contains all the `DataTable` objects in a `DataSet`.  
  
 A `DataTable` is defined in the `System.Data` namespace and represents a single table of memory-resident data. It contains a collection of columns represented by a `DataColumnCollection`, and constraints represented by a `ConstraintCollection`, which together define the schema of the table. A `DataTable` object also contains a collection of rows represented by the `DataRowCollection`, which contains the data in the table. Along with its current state, a `DataRow` object retains both its current and original versions to identify changes to the values stored in the row.  
  
## See Also  
 [ADO.NET DataSet for Host Integration Server](../HIS2010/ado-net-dataset-for-host-integration-server1.md)   
 [Managed Provider Programmer's Guide](../HIS2010/managed-provider-programmer-s-guide1.md)