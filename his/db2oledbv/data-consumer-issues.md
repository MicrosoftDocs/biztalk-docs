---
title: "Data Consumer Issues | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 596564f9-ad8a-4c56-915f-1a4ff2a4e110
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Consumer Issues
This topic provides information to troubleshoot data consumer issues.  

## SQL Server Integration Services  

### Enterprise Single Sign-On  
 When using Enterprise Single Sign-On with SQL Server Integration Services, you may need to enter a placeholder value of “MS$SAME” for user name and password. Using Data Links, you can configure ESSO for use with SSIS.  

1.  In the **Connection** dialog, click **Single sign-on** for the **Security method**.  

2.  Select an **Affiliate application** from the drop-down list box.  

3.  In the **All** dialog, click **Password** and then click Edit Value. In the **Edit Property Value** dialog, enter **MS$SAME** for the **Property Value**, and click **OK**.  

4.  In the **All** dialog, click **User ID** and then click **Edit Value**. In the **Edit Property Value** dialog, enter **MS$SAME** for the **Property Value**, and click **OK**.  

5.  In the **Connection** dialog, click **Test**. You can view the results in the Microsoft Data Links dialog.  

6.  Click **OK** to save the configuration information.  

### FastLoad to insert TIMESTAMP value  
 When using SQL Server Integration Services OLE DB Destination with FastLoad to insert SQL Server datetime or datetime2 values into a DB2 TIMESTAMP column, you may encounter this error.  

 THE STRING REPRESENTATION OF A DATETIME VALUE IS NOT A VALID DATETIME VALUE  

 To work-around this problem, you should set the Data Provider data source property Use Early Metadata to true.  

```  
Use Early Metadata=True  
```  

### Data Type Mapping  
 When using the SQL Server Integration Services Import and Export Wizards, from the Microsoft SQL Server Management Studio or Business Intelligence Design Studio, you can customize the default data conversions by editing XML mapping files. The Import and Export Wizard XML mapping files are located in the following folder.  

```  
C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles  
```  

```  
C:\Program Files (x86)\Microsoft SQL Server\100\DTS\MappingFiles  
```  

 To correctly map IBM DB2 for i5/OS character and decimal data types to SQL Server data types, the data mapping files should be extended to include the DB2 data type long form synonym. For example, add the following data type mapping between DB2 INTEGER source and SQL Server. This mapping is compatible with SQLOLEDB, SQLNCL, SQLNCLI10, and System.Data.SqlClient.SqlConnection. It replaces the short form SourceDataType value INT with the long form INTEGER.  

 The following mapping for DB2 INT is compatible with a DB2 for z/OS V9 source.  

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

 The following data type mapping for DB2 INTEGER is compatible with a DB2 for i5/OS V6R1 source.  

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

### Data Type Mapping Files  
 The following table describes the three mapping files that you can edit when you use the Data Provider.  

|DB2 Data Type Name|DB2ToMSSql|DB2ToMSSql10|DB2ToSSIS10|  
|------------------------|----------------|------------------|-----------------|  
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
|INT|INT|INT|DT_14|  
|INTEGER|INT|INT|DT_14|  
|BIGINT|BIGINT|BIGINT|DT_18|  
|DECIMAL|NUMERIC|NUMERIC|DT_NUMERIC|  
|NUMERIC|NUMERIC|NUMERIC|DT_NUMERIC|  
|REAL|REAL|REAL|DT_R4|  
|FLOAT|FLOAT|FLOAT|DT_R8|  
|DOUBLE|FLOAT|FLOAT|DT_R8|  
|DOUBLE PRECISION|FLOAT|FLOAT|DT_R8|  
|BLOB|image|image|DT_BYTES|  
|BINARY LARGE OBJECT|image|image|DT_BYTES|  
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

 For more information about configuring SQL Server 2008 Integration Services, see the Importing and Exporting Data by Using the SQL Server Import and Export Wizard) topic in [SQL Server Books Online](http://go.microsoft.com/fwlink/?LinkId=193204) (http://go.microsoft.com/fwlink/?LinkId=193204).  

### Customizing Data Flow Components  
 You can use SQL Server Integration Services Data Flow Components to perform default and customized transformations. The customized transformations are based on developer-provided custom code.  

 The SQL Server Integration Services mapping files in XML format are for use with the Import and Export Wizard. These files are not for use with the Data Flow. SQL Server Integration Services offers a Pipeline Buffer class to allow enterprise developers to customize data mapping within the Data Flow. For more information about customizing data flow components using SQL Server 2008 Integration Services, see the Working with Data Types in the Data Flow topic in [SQL Server Books Online](http://go.microsoft.com/fwlink/?LinkId=241523) (http://go.microsoft.com/fwlink/?LinkId=241523).  

## SQL Server Replication  

### Derive Parameters  
 SQL Server Replication requires that Derive Parameter is set to FALSE.  

### Data Type Mapping  
 SQL Server Replication may convert data incorrectly, based on the default mappings from SQL Server to DB2 data types. We recommend that you review and revise the Replication data type mappings using the following SQL Server system stored procedures.  

- ```  
  sp_helpdatatypemap  
  ```  

- ```  
  sp_getdefaultdatatypemapping  
  ```  

- ```  
  sp_setdefaultdatatypemapping  
  ```  

  For more information, see the System Stored Procedures \(Transact\-SQL\) topic in SQL Server Books Online \([http:\/\/go.microsoft.com\/fwlink\/?LinkId\=241524](http://go.microsoft.com/fwlink/?LinkId=241524)\).  

  Problem with mapping SQL Server DATETIME2 to DBTYPE\_TIMESTAMP  

  SQL Server 2008 Replication to DB2 for z\/OS may fail with SQLCODE \-188 \(the string representation of a datetime value is not a valid datetime value\). This occurs when Replication is configured to map DATETIME2 to DB2 VARCHAR\(27\) and uses subscription article commands with string literal data values.  

  Solution to problem with Step\-by\-Step Instructions  

  Re\-configure SQL Server 2008 Replication to map DATETIME2 to DB2 TIMESTAMP and subscription article commands with parameters. This enables the Data Provider to format the DATETIME2 as a DB2 TIMESTAMP structure that is supported by the IBM DB2 database server.  

1. Identify the data type mapping to modify. Use MASTER for all steps.  

    **select \* from**  

   ```  
   sys.fn_helpdatatypemap  
   (  
      'MSSQLSERVER',   
       '%',   
       '%',   
       '%',   
       '%',   
       '%',   
       0  
   )  
   ```  

2. Where destination\_dbms \= 'DB2' and source\_type \= 'datetime2'The results should indicate the mapping\_id to modify. The following table shows the results pane for this example where the mapping\_id is 189.  


   | mapping\_id | source\_dbms | source\_type | destination\_dbms | destination\_type | destination\_length |
   |-------------|--------------|--------------|-------------------|-------------------|---------------------|
   |     189     | MSSQLSERVER  |  datetime2   |        DB2        |      VARCHAR      |         27          |


3. Drop the data type mapping.  

   ```  
   exec sp_dropdatatypemapping 189  
   ```  

4. Add the data type mapping.  

   ```  
   exec  sp_adddatatypemapping  
        @source_dbms = 'MSSQLSERVER',   
        @source_type = 'datetime2',   
        @destination_dbms = 'DB2',   
        @destination_type = 'TIMESTAMP',   
        @destination_nullable = 1,   
        @destination_createparams = 0,   
        @dataloss = 0,   
        @is_default = 1  
   ```  

5. Run the query again to verify the new data type mapping.  

    **select \* from**  

   ```  
   select * from sys.fn_helpdatatypemap  
   (  
      'MSSQLSERVER',   
       '%',   
       '%',   
       '%',   
       '%',   
       '%',   
       0  
   )  
   ```  

6. Where destination\_dbms \= 'DB2' and source\_type \= 'datetime2'  

    The results should indicate the mapping\_id to modify. The following table shows the results pane for this example where the mapping\_id is 189.  


   | mapping\_id | source\_dbms | source\_type | destination\_dbms | destination\_type | destination\_length |
   |-------------|--------------|--------------|-------------------|-------------------|---------------------|
   |     494     | MSSQLSERVER  |  datetime2   |        DB2        |     TIMESTAMP     |        NULL         |


7. Identify the replication subscription article to re\-configure. Use the Transact\-SQL USE statement to switch from the master database to the database from which you are replicating.  

    **USE \[Test\]**  

   ```  
   select name, status from sysarticles  
   ```  

8. The results should display the name of the article to modify. In this example, the following table shows the results where the name is DB2TS01.  


   |  name   | status |
   |---------|--------|
   | DB2TS01 |   25   |


9. If the status value is 1 or 9, then the article is configured for string literal formatting.  

     If the status value is 17 or 25, then the article is configured for parameterized formatting.  

10. Configure the replication subscription article for parameterized commands.  

     **USE \[Test\]**  

    ```  
    DECLARE @publication AS sysname;   
    DECLARE @article AS sysname;   
    SET @publication = N'DB2TS_PUB01';   
    SET @article = N'DB2TS01';   
    EXEC sp_changearticle @publication, @article, 'status', 'parameters', 0, 0;  
    ```  

    For more information, see [Replication System Stored Procedures Concepts](http://go.microsoft.com/fwlink/?LinkId=241525) (http://go.microsoft.com/fwlink/?LinkId=241525) in SQL Server Books Online.  

### SQL Server Analysis Services  
 When you design cubes for use with SQL Server Analysis Services, the tools generate SQL commands that contain long alias names that may exceed the maximum length supported by the DB2 server. Depending on the DB2 platform and version that you use, you may not be able to use queries with alias names exceeding 18 characters. For example, many objects deployed in DB2 for z/OS use names of 18 characters. Refer to the DB2 SQL Reference for your DB2 platform and version and check with your DB2 database administrator. We recommend that the administrator or developer update the two SQL Server Analysis Service configuration cartridge files that contain the data type mapping support for DB2 by changing the identifier-length (limit-table-identifier-length) from 29 to 18. The following are the names and location of the two cartridge files that must be updated.  

- C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE\DataWarehouseDesigner\UIRdmsCartridge\db2v0801.xs  

- C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE\DataWarehouseDesigner\UIRdmsCartridge\db2v0801.xs  

  SQL Server Analysis Services uses the updated configuration files to correctly name objects in SQL commands.