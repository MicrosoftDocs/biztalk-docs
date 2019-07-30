---
title: "Updating the DB2 Database with a Data Adapter and the Dataset1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3b85eac-76b8-450d-adcc-8ee63510bccb
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Updating the DB2 Database with a Data Adapter and the Dataset
The `Update` method of `MsDb2DataAdapter` is called to resolve changes from a dataset back to the data source. The `Update` method, like the `Fill` method, takes as arguments an instance of `DataSet`, and an optional `DataTable` object or `DataTable` name. The `DataSet` instance is the `DataSet` object that contains the changes that have been made, and the `DataTable` object identifies the table from which to retrieve the changes.  
  
## Calling the Update Method  
 When you call the `Update` method, `MsDb2DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE). When the `MsDb2DataAdapter` encounters a change to a data row, it uses `InsertCommand`, `UpdateCommand`, or `DeleteCommand` to process the change. This enables you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, with stored procedures. You must explicitly set the commands before calling `Update`. If `Update` is called, and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown. You can use command parameters to specify input and output values for an SQL statement or stored procedure for each modified row in a dataset.  
  
 If your `DataTable` object maps to or is generated from a single database table, you can take advantage of the `MsDb2CommandBuilder` object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` properties of the `MsDb2DataAdapter` object.  
  
### Updating Datasets  
 The `Update` method resolves your changes back to the data source; however other clients might have modified data at the data source since the last time you filled the dataset. To update your dataset with current data, use the `MsDb2DataAdapter` and `Fill` method. New rows are added to the table, and updated information is incorporated into existing rows. The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the dataset and the rows returned by `SelectCommand`. If the `Fill` method encounters a primary key value for a row in the dataset that matches a primary key value from a row in the results returned by `SelectCommand`, it updates the existing row with the information from the row returned by `SelectCommand` and sets the `RowState` property of the existing row to `Unchanged`. If a row returned by `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the dataset, the `Fill` method adds a new row with a `RowState` of `Unchanged`.  
  
> [!NOTE]
>  If `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` object does not set a PrimaryKey value for the resulting `DataTable` object. You must define the PrimaryKey yourself to ensure that duplicate rows are resolved correctly.  
  
 To handle exceptions that might occur when you call the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur, or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete.  
  
> [!NOTE]
>  Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` objects causes all Original values for a data row to be overwritten with the Current values for the data row. If the field values that identify the row as unique have been modified, after you call `AcceptChanges`, the Original values no longer match the values in the data source.  
  
## Working with Auto-Incrementing Columns  
 If the tables from your data source have auto-incrementing columns, you can fill the columns in your dataset either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, or by using the `RowUpdated` event of the `MsDb2DataAdapter`.  
  
 However, the values in your dataset can become out of sync with the values at the data source and result in unexpected behavior. For example, consider a table that has an auto-incrementing primary key column of CustomerID. If you add two new customers within the dataset, they receive auto-incremented CustomerId values of 1 and 2. When the second customer row is passed to the `Update` method of `MsDb2DataAdapter`, the newly added row receives an auto-incremented CustomerID value of 1 at the data source, which does not match the value, 2, in the dataset. When the `MsDb2DataAdapter` fills the row in the dataset with the returned value, a constraint violation occurs because the first customer row already has a CustomerID of 1.  
  
 To avoid this behavior, we recommend that, when you are working with auto-incrementing columns at a data source and auto-incrementing columns in a dataset, you create the column in the dataset with an AutoIncrementStep of -1 and an AutoIncrementSeed of 0, and also ensure that your data source generates auto-incrementing Identity values starting at 1 and incrementing with a positive step value. As a result, the dataset will generate negative numbers for auto-incremented values that do not conflict with the positive auto-increment values generated by the data source. Another option is to use columns of type `Guid` instead of auto-incrementing columns. The algorithm that generates `Guid` values should never generate the same `Guid` in the dataset as is generated by the data source.  
  
 In many circumstances, the order in which changes that are made through the dataset are sent to the data source is important. For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value, it is important to process the update before the insert.  
  
 You can use the `Select` method of the `DataTable` object to return a `DataRow` array that only references rows with a particular `RowState`. You can then pass the returned `DataRow` array to the `Update` method of the `MsDb2DataAdapter` to process the modified rows. By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.  
  
## See Also  
 [Working with the DataAdapter and the DataSet for a DB2 Database](../core/working-with-the-dataadapter-and-the-dataset-for-a-db2-database1.md)