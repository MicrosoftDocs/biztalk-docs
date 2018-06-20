---
title: "SQL Server Replication (Troubleshooting)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd95c5eb-8b39-4b3e-bf1e-2f8ba7496c12
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SQL Server Replication (Troubleshooting)
This topic contains the following sections relating to troubleshooting issues between the OLE DB Provider for DB2 and SQL Server (Data Provider) and SQL Server.  
  
 [Incorrect Data Type Mappings](../core/sql-server-replication-troubleshooting-1.md#datatype)  
  
 [Failure to replicate DATETIME2 columns to DB2 TIMESTAMP columns](../core/sql-server-replication-troubleshooting-1.md#datetime2)  
  
 For more information about SQL Server Replication, see [Developer’s Guide (Replication)](http://go.microsoft.com/fwlink/?LinkId=193231) (http://go.microsoft.com/fwlink/?LinkId=193231) in SQL Server Books Online.  
  
##  <a name="datatype"></a> Incorrect Data Type Mappings  
 SQL Server Replication may convert data incorrectly, based on the default mappings from SQL Server to DB2 data types. We recommend that the administrator and developer review and revise the Replication data type mappings using the following SQL Server system stored procedures.  
  
 **sp_helpdatatypemap**  
  
 **sp_getdefaultdatatypemapping**  
  
 **sp_setdefaultdatatypemapping**  
  
 For more information, see the [System Stored Procedures (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=180765\)) topic in SQL Server Books Online (<http://go.microsoft.com/fwlink/?LinkID=180765>).  
  
##  <a name="datetime2"></a> Failure to replicate DATETIME2 columns to DB2 TIMESTAMP columns  
 **Problem**  
  
 SQL Server 2008 Replication to DB2 for z/OS may fail with SQLCODE -188 (the string representation of a datetime value is not a valid datetime value). This occurs when Replication is configured to map DATETIME2 to DB2 VARCHAR(27) and uses subscription article commands with string literal data values.  
  
 **Solution**  
  
 Re-configure SQL Server 2008 Replication to map DATETIME2 to DB2 TIMESTAMP and subscription article commands with parameters. This enables the Data Provider to format the DATETIME2 as a DB2 TIMESTAMP structure that is supported by the IBM DB2 database server.  
  
 **Step by Step Instructions**  
  
 **Step 1**. Identify the data type mapping to modify. `USE MASTER` for all steps.  
  
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
where destination_dbms = 'DB2' and source_type = 'datetime2'  
  
```  
  
 The results should indicate the mapping_id to modify. The following table shows the results pane for this example where the mapping_id is 189.  
  
|||||||  
|-|-|-|-|-|-|  
|mapping_id|source_dbms|source_type|destination_dbms|destination_type|destination_length|  
|189|MSSQLSERVER|datetime2|DB2|VARCHAR|27|  
  
 **Step 2**. Drop the data type mapping.  
  
```  
exec sp_dropdatatypemapping  189  
```  
  
 **Step 3**. Add the data type mapping.  
  
```  
exec  sp_adddatatypemapping   
    @source_dbms                  = 'MSSQLSERVER',    
    @source_type                  = 'datetime2',  
    @destination_dbms             = 'DB2',  
    @destination_type             = 'TIMESTAMP',  
    @destination_nullable         = 1,  
    @destination_createparams     = 0,  
    @dataloss                     = 0,  
    @is_default                   = 1  
  
```  
  
 **Step 4**. Run the query again to verify the new data type mapping.  
  
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
where destination_dbms = 'DB2' and source_type = 'datetime2'  
  
```  
  
 The results should display the new data type mapping. In this example, the mapping_id shown in the following table is 189.  
  
|||||||  
|-|-|-|-|-|-|  
|mapping_id|source_dbms|source_type|destination_dbms|destination_type|destination_length|  
|494|MSSQLSERVER|datetime2|DB2|TIMESTAMP|NULL|  
  
 **Step 5.** Identify the replication subscription article to re-configure. Use the Transact-SQL `USE` statement to switch from the master database to the database from which you are replicating.  
  
```  
USE [Test]  
select name, status from sysarticles  
```  
  
 The results should display the name of the article to modify. In this example, the following table shows the results where the name is DB2TS01.  
  
|||  
|-|-|  
|name|status|  
|DB2TS01|25|  
  
 If the status value is 1 or 9, then the article is configured for string literal formatting.  
  
 If the status value is 17 or 25, then the article is configured for parameterized formatting.  
  
 **Step 6**. Configure the replication subscription article for parameterized commands.  
  
```  
USE [Test]  
DECLARE @publication AS sysname;  
DECLARE @article AS sysname;  
SET @publication = N'DB2TS_PUB01';  
SET @article = N'DB2TS01';  
  
EXEC sp_changearticle @publication, @article, 'status' , 'parameters' , 0 , 0;  
  
```  
  
 For more information, see [Replication System Stored Procedures Concepts](http://go.microsoft.com/fwlink/?LinkId=193232) (http://go.microsoft.com/fwlink/?LinkId=193232) in SQL Server Books Online.