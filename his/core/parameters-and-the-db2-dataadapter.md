---
title: "Parameters and the DB2 DataAdapter1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: caf23cff-cea3-4307-8b8d-35eadbcabe90
caps.latest.revision: 3
---
# Parameters and the DB2 DataAdapter
The `DataAdapter` class has four properties that are used to retrieve data from and update data to the data source: the `SelectCommand` property returns data from the data source; the `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties are used to manage changes at the data source. You must set the `SelectCommand` property before calling the `Fill` method of the `DataAdapter` object. The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the `DataSet`. For example, if rows have been added, you must set the `InsertCommand` property before calling the `Update` method. When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` object uses the respective `Command` property to process the action. Current information about the modified row is passed to the `Command` object through the `Parameters` collection.  
  
 When you are updating a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated. The unique identifier is commonly the value of a primary key field. The UPDATE statement uses parameters that contain both the unique identifier, and the columns and values to be updated.  
  
 Specifying the `Parameter` type converts the value of the Parameter to the Managed Provider for DB2 before passing the value to the data source. You may also specify the type of a `Parameter` in a generic fashion by setting the `DbType` property of the `Parameter` object to a particular `DbType`.  
  
## ParameterDirection Enumeration Values  
 The following table shows the values you can use with the `ParameterDirection` enumeration to set the `Direction` of the `Parameter`.  
  
|Member name|Description|  
|-----------------|-----------------|  
|Input|The parameter is an input parameter. This is the default.|  
|InputOutput|The parameter is capable of both input and output.|  
|Output|The parameter is an output parameter.|  
|ReturnValue|The parameter represents a return value.|  
  
 `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`. The `SourceColumn` is the name of the `DataColumn` from the `DataRow` where the value of the `Parameter` is retrieved. The `SourceVersion` specifies which `DataRow` version the `DataAdapter` uses to retrieve the value.  
  
## DataRowVersion Enumeration Values  
 The following table shows the `DataRowVersion` enumeration values available for use with `SourceVersion`.  
  
|Member name|Description|  
|-----------------|-----------------|  
|Current|The parameter uses the current value of the column. This is the default.|  
|Default|The parameter uses the DefaultValue of the column.|  
|Original|The parameter uses the original value of the column.|  
|Proposed|The parameter uses a proposed value.|  
  
 You can control how the values returned from the data source are mapped back to the `DataSet` object by using the `UpdatedRowSource` property of the `Command` object. By setting the `UpdatedRowSource` property to one of the `UpdateRowSource` enumeration values, you can control whether parameters returned by the `DataAdapter` command are ignored or applied to the changed row in the `DataSet` object. You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataSet` object.  
  
## UpdateRowSource Enumeration Values  
 The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter` object.  
  
|Member name|Description|  
|-----------------|-----------------|  
|Both|Both the output parameters and the first row of a returned result set can be mapped to the changed row in the `DataSet`.|  
|ReturnedFirstRecord|Only the data in the first row of a returned result set can be mapped to the changed row in the `DataSet`.|  
|None|Any output parameters or rows of a returned result set are ignored.|  
|OutputParameters|Only output parameters may be mapped to the changed row in the `DataSet`.|  
  
## See Also  
 [Working with the DataAdapter and the DataSet for a DB2 Database](../core/working-with-the-dataadapter-and-the-dataset-for-a-db2-database.md)