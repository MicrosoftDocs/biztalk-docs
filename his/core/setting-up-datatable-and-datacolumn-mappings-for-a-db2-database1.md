---
description: "Learn more about: Setting up DataTable and DataColumn Mappings for a DB2 Database"
title: "Setting up DataTable and DataColumn Mappings for a DB2 Database1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Setting up DataTable and DataColumn Mappings for a DB2 Database
An `MsDb2DataAdapter` contains a collection of zero or more `DataTableMapping` objects in its `TableMappings` property. A `DataTableMapping` object provides a master mapping between the data returned from a query against a data source, and a `DataTable` object. The `DataTableMapping` name can be passed instead of the `DataTable` name to the `Fill` method of the `MsDb2DataAdapter`.  
  
 A `DataTableMapping` object enables you to use column names in a `DataTable` object that are different from those in the database. The `MsDb2DataAdapter` uses the mapping to match the columns when the table is updated.  
  
 If you do not specify a `TableName` or a `DataTableMapping` name when calling the `Fill` or `Update` method of the `MsDb2DataAdapter`, the `MsDb2DataAdapter` looks for a `DataTableMapping` named "Table". If that `DataTableMapping` does not exist, the `TableName` of the `DataTable` object is "Table". You can specify a default `DataTableMapping` by creating a `DataTableMapping` with the name of "Table".  
  
 When the `Fill` method is passed an instance of a `DataSet` and a `DataTableMapping` name, and if a mapping with that name exists, it is used; otherwise, a `DataTable` object with that name is used.  
  
> [!NOTE]
>  If a source column name is not supplied for a column mapping, or a source table name is not supplied for a table mapping, default names are automatically generated. If no source column is supplied for a column mapping, the column mapping is given an incremental default name of SourceColumnN, starting with SourceColumn1. If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of SourceTableN, starting with SourceTable1.  
  
> [!NOTE]
>  We recommend that you avoid the naming convention of SourceColumnN for a column mapping, or SourceTableN for a table mapping, because the name you supply may conflict with an existing default column mapping name in the `ColumnMappingCollection` or table mapping name in the `DataTableMappingCollection`. If the supplied name already exists, an exception is thrown.  
  
 If `SelectCommand` returns multiple tables, `Fill` automatically generates table names with incremental values for the tables in the dataset, starting with the specified table name and continuing on in the form TableNameN, starting with TableName1. You can use table mappings to map the automatically generated table name to a name you want specified for the table in the dataset.  
  
## See Also  
 [Working with the DataAdapter and the DataSet for a DB2 Database](../core/working-with-the-dataadapter-and-the-dataset-for-a-db2-database1.md)   
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db21.md)
