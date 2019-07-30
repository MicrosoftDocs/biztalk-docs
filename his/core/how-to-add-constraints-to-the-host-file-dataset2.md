---
title: "How to Add Constraints to the Host File Dataset2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d7cef34-abad-4bf8-b0cc-7349bd2389a2
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Add Constraints to the Host File Dataset
The `HostFileDataAdapter.Fill method` fills a `DataSet` object with table columns and rows from a data source; though constraints are commonly set by the data source, the `Fill` method does not add this schema information to the `DataSet` object by default. To populate a `DataSet` object with existing primary key constraint information from a data source, you can call `HostFileDataAdapter.FillSchema`.  
  
> [!NOTE]
>  If a `column` in a data source is identified as auto-incrementing, the `FillSchema` method, or the `Fill` method with a `MissingSchemaAction` of `AddWithKey`, creates a `DataColumn` that has an `AutoIncrement` property set to `true`. However, you must set the `AutoIncrementStep` and `AutoIncrementSeed` values yourself.  
  
### To populate a dataset with additional key constraints  
  
1.  Call `HostFileDataAdapter.FillSchema`, using the targeted `DataSet` and Schema that contains the specified key constraints.  
  
     Adding schema information to a `DataSet` before filling it with data ensures that primary key constraints are included with the `DataTable` objects in the `DataSet` object. As a result, when additional calls to fill the `DataSet` are made, the primary key column information is used to match new rows from the data source with current rows in each `DataTable` object, and current data in the tables is overwritten with data from the data source. Without the schema information, the new rows from the data source are appended to the `DataSet` object, resulting in duplicate rows.  
  
## See Also  
 [Working with the Host File Adapter and Dataset](../core/working-with-the-host-file-adapter-and-dataset2.md)   
 [BizTalk Adapter for Host Files Configuration](./biztalk-adapter-for-host-files-configuration1.md)