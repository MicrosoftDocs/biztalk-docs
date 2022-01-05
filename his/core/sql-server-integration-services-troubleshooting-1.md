---
description: "Learn more about: SQL Server Integration Services (Troubleshooting)"
title: "SQL Server Integration Services (Troubleshooting)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5aebf5f8-f606-40ce-9c08-78af833ded4a
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# SQL Server Integration Services (Troubleshooting)
You can customize the default data conversions by using the SQL Server Integration Services Import and Export Wizard to edit data type mapping files. The mapping files define data type mappings between the data source and the destination, and are defined in XML format. When you edit the XML files, you ensure compatibility between the source and destination.

 The XML files are located in the following folders.

 C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles

 C:\Program Files (x86)\Microsoft SQL Server\100\DTS\MappingFiles

## Data Type Mapping
 To correctly map IBM DB2 for i5/OS character and decimal data types to SQL Server data types, the data mapping files should be extended to include the DB2 data type long form synonym. For example, when you use the Microsoft OLE DB Provider for DB2 (Data Provider), add the following data type mapping between DB2 INTEGER source and SQL Server. This mapping is compatible with SQLOLEDB, SQLNCL, SQLNCLI10, and `System.Data.SqlClient.SqlConnection`. It replaces the short form SourceDataType value **INT** with the long form **INTEGER**.

 The following mapping for DB2 INT is compatible with a DB2 for z/OS source.

```
<!-- INT -->
    <dtm:DataTypeMapping>
        <dtm:SourceDataType>
            <dtm:DataTypeName>INT</dtm:DataTypeName>
        </dtm:SourceDataType>
        <dtm:DestinationDataType>
            <dtm:SimpleType>
                <dtm:DataTypeName>INT</dtm:DataTypeName>
            </dtm:SimpleType>
        </dtm:DestinationDataType>
    </dtm:DataTypeMapping>

```

 The following data type mapping for DB2 INTEGER is compatible with a DB2 for i5/OS source.

```
<!-- INTEGER -->
<dtm:DataTypeMapping>
    <dtm:SourceDataType>
        <dtm:DataTypeName>INTEGER</dtm:DataTypeName>
    </dtm:SourceDataType>
    <dtm:DestinationDataType>
        <dtm:SimpleType>
            <dtm:DataTypeName>INT</dtm:DataTypeName>
        </dtm:SimpleType>
    </dtm:DestinationDataType>
</dtm:DataTypeMapping>

```

### Mapping Files
 The following table describes the three mapping files that you can edit when you use the Data Provider.

|DB2 Data Type Name|DB2ToMSSql|DB2ToMSSql10|DB2ToSSIS10|
|-|-|-|-|
|TIME|DATETIME|time|DT_DBTIME|
|TIMESTAMP|datetime|datetime2|DT_DBTIMESTAMP2|
|DATE|DATETIME|DATE|DT_DBDATE|
|CHAR|CHAR|CHAR|DT_STR|
|CHAR () FOR BIT DATA|BINARY|BINARY|DT_BYTES|
|CHAR () FOR MIXED DATA|NCHAR|NCHAR|DT_WSTR|
|CHAR () FOR SBCS DATA|CHAR|CHAR|DT_STR|
|CHARACTER|CHAR|CHAR|DT_STR|
|CHARACTER () FOR BIT DATA|BINARY|BINARY|DT_BYTES|
|CHARACTER () FOR MIXED DATA|NCHAR|NCHAR|DT_WSTR|
|CHARACTER () FOR SBCS DATA|CHAR|CHAR|DT_STR|
|NATIONAL CHARACTER|NCHAR|NCHAR|DT_WSTR|
|VARCHAR|VARCHAR|VARCHAR|DT_STR|
|VARCHAR () FOR BIT DATA|VARBINARY|VARBINARY|DT_BYTES|
|VARCHAR () FOR MIXED DATA|NVARCHAR|NVARCHAR|DT_WSTR|
|VARCHAR () FOR SBCS DATA|VARCHAR|VARCHAR|DT_STR|
|CHARACTER VARYING|VARCHAR|VARCHAR|DT_STR|
|CHARACTER VARYING () FOR BIT DATA|VARBINARY|VARBINARY|DT_BYTES|
|CHARACTER VARYING () FOR MIXED DATA|NVARCHAR|NVARCHAR|DT_WSTR|
|CHARACTER VARYING () FOR SBCS DATA|VARCHAR|VARCHAR|DT_STR|
|NATIONAL CHARACTER VARYING|NVARCHAR|NVARCHAR|DT_WSTR|
|LONG VARCHAR FOR BIT DATA|image|image|DT_IMAGE|
|LONG VARCHAR|text|text|DT_TEXT|
|GRAPHIC|NCHAR|NCHAR|DT_WSTR|
|VARGRAPHIC|NVARCHAR|NVARCHAR|DT_WSTR|
|GRAPHIC VARYING|NVARCHAR|NVARCHAR|DT_WSTR|
|SMALLINT|SMALLINT|SMALLINT|DT_I2|
|INT|INT|INT|DT_I4|
|INTEGER|INT|INT|DT_I4|
|BIGINT|BIGINT|BIGINT|DT_I8|
|DECIMAL|NUMERIC|NUMERIC|DT_NUMERIC|
|NUMERIC|NUMERIC|NUMERIC|DT_NUMERIC|
|REAL|REAL|REAL|DT_R4|
|FLOAT|FLOAT|FLOAT|DT_R8|
|DOUBLE|FLOAT|FLOAT|DT_R8|
|DOUBLE PRECISION|FLOAT|FLOAT|DT_R8|
|BLOB|image|image|DT_BYTES|
|BNARY LARGE OBJECT|image|image|DT_BYTES|
|CLOB|text|text|DT_TEXT|
|CLOB () FOR MIXED DATA|ntext|ntext|DT_NTEXT|
|CLOB () FOR SBCS DATA|text|text|DT_TEXT|
|CHAR LARGE OBJECT|text|text|DT_TEXT|
|CHAR LARGE OBJECT () FOR MIXED DATA|ntext|ntext|DT_NTEXT|
|CHAR LARGE OBJECT () FOR SBCS DATA|text|text|DT_TEXT|
|CHARACTER LARGE OBJECT|text|text|DT_TEXT|
|CHARACTER LARGE OBJECT () FOR MIXED DATA|ntext|ntext|DT_NTEXT|
|CHARACTER LARGE OBJECT () FOR SBCS DATA|text|text|DT_TEXT|
|130|ntext|ntext|DT_NTEXT|

 After you edit a mapping file, you must close and reopen the SQL Server Import and Export Wizard or the Business Intelligence Development Studio, depending on the environment in which you are working.

 For more information about configuring SQL Server 2008 Integration Services, see the [Importing and Exporting Data by Using the SQL Server Import and Export Wizard](/previous-versions/sql/sql-server-2008-r2/ms141209(v=sql.105))) topic in SQL Server Books Online (https://go.microsoft.com/fwlink/?LinkId=193204).

### Customizing Data Flow Components
 You can use SQL Server Integration Services Data Flow Components to perform default and customized transformations. The customized transformations are based on developer-provided custom code.

 The SQL Server Integration Services mapping files in XML format are for use with the Import and Export Wizard. These files are not for use with the Data Flow. SQL Server Integration Services offers a Pipeline Buffer class to allow enterprise developers to customize data mapping within the Data Flow.

 For more information about customizing data flow components using SQL Server 2008 Integration Services, see the [Working with Data Types in the Data Flow](/previous-versions/sql/sql-server-2008-r2/ms345165(v=sql.105)) topic in SQL Server Books Online (https://go.microsoft.com/fwlink/?LinkId=193208).