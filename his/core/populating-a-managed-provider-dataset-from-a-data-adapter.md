---
title: "Populating a Managed Provider Dataset from a Data Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88d1695a-cd34-496e-967d-4527b4b9c516
caps.latest.revision: 3
---
# Populating a Managed Provider Dataset from a Data Adapter
The dataset is a memory-resident representation of data that provides a consistent relational programming model independent of the data source. The dataset represents a complete set of data including tables, constraints, and relationships among the tables. Because the dataset is independent of the data source, a dataset can include data that is local to the application, and also data from multiple data sources. Interaction with existing data sources is controlled through an `MsDb2DataAdapter` object.  
  
 The <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataAdapter.SelectCommand%2A?displayProperty=fullName> is a `Command` object that retrieves data from the data source. The `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataAdapter> are also `Command` objects that manage updates to the data in the data source according to modifications made to the data in the dataset.  
  
## Fill Method  
 The `MsDb2DataAdapter.Fill` method is used to populate a dataset with the results of <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataAdapter.SelectCommand%2A?displayProperty=fullName>. `Fill` takes as its arguments a `DataSet` object to be populated, and a `DataTable` object, or the name of the `DataTable` object to be filled with the rows returned from `SelectCommand`.  
  
 The `Fill` method uses <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> implicitly to return the column names and types that are used to create the tables in the dataset, and also the data to populate the rows of the tables in the dataset. Tables and columns are only created if they do not already exist; otherwise `Fill` uses the existing dataset schema. Column types are created as .NET Framework types. Primary keys are not created unless they are located in the data source, and `DataAdapter.MissingSchemaAction` is set to `MissingSchemaAction.AddWithKey`. If `Fill` finds that a primary key exists for a table, it overwrites data in the `DataSet` with data from the data source for rows where the primary key column values match those of the row returned from the data source. If no primary key is found, the data is appended to the tables in the `DataSet. Fill` uses any mappings that may exist when populating the `DataSet` object.  
  
> [!NOTE]
>  If `SelectCommand` returns the results of an OUTER JOIN, the `MsDb2DataAdapter` does not set a PrimaryKey value for the resulting `DataTable`. You must define the PrimaryKey yourself to ensure that duplicate rows are resolved correctly  
  
## Multiple Result Sets  
 If <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataAdapter> encounters multiple result sets, it creates multiple tables in the dataset. The tables are given an incremental default name of TableN, starting with "Table" for Table0. If a table name is passed as an argument to the `Fill` method, the tables are given an incremental default name of TableNameN, starting with "TableName" for TableName0.  
  
 Any number of <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataAdapter> objects can be used with a dataset. Each <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataAdapter> can be used to fill one or more `DataTable` objects and resolve updates back to the relevant data source. You can add `DataRelation` and `Constraint` objects to the dataset locally, enabling you to relate data from dissimilar data sources.  
  
## See Also  
 [Working with the DataAdapter and the DataSet for a DB2 Database](../core/working-with-the-dataadapter-and-the-dataset-for-a-db2-database.md)   
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db2.md)