---
title: "Adding Constraints to a DB2 DataSet2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2513167e-014a-4013-9aa2-bcbd955e6cff
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Adding Constraints to a DB2 DataSet
The `Fill` method of the `MsDb2DataAdapter` fills a dataset only with table columns and rows from a data source; though constraints are commonly set by the data source, the `Fill` method does not add this schema information to the dataset by default. To populate a dataset with existing primary key constraint information from a data source, you can either call the `FillSchema` method of the `MsDb2DataAdapter`, or set the `MissingSchemaAction` property of the `MsDb2DataAdapter` to `AddWithKey` before calling `Fill`. This ensures that primary key constraints in the dataset reflect those at the data source. Foreign key constraint information is not included and must be created explicitly.  
  
 Adding schema information to a `DataSet` object before filling it with data ensures that primary key constraints are included with the `DataTable` objects in the `DataSet` object. As a result, when additional calls to fill the `DataSet` are made, the primary key column information is used to match new rows from the data source with current rows in each `DataTable` object, and current data in the tables is overwritten with data from the data source. Without the schema information, the new rows from the data source are appended to the `DataSet`, resulting in duplicate rows.  
  
> [!NOTE]
>  If a column in a data source is identified as auto-incrementing, the `FillSchema` method, or the `Fill` method with a `MissingSchemaAction` of `AddWithKey`, creates a `DataColumn` with an `AutoIncrement` property set to `true`. However, you must set the `AutoIncrementStep` and `AutoIncrementSeed` values yourself.  
  
 Using the `FillSchema` method or setting the `MissingSchemaAction` to `AddWithKey` requires extra processing at the data source to determine primary key column information. This additional processing can hinder performance. If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.  
  
 If the `MsDb2DataAdapter` encounters multiple result sets returned from the `SelectCommand` property, it creates multiple tables in the dataset. The tables are given a zero-based incremental default name of TableN, starting with Table instead of "Table0". If a table name is passed as an argument to the `FillSchema` method, the tables are given a zero-based incremental name of TableNameN, starting with TableName instead of "TableName0".