---
title: "Operations on Interface Tables and Interface Views | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c7f3453-848f-42df-b092-725d9ff466cf
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Interface Tables and Interface Views
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] surfaces a set of standard operations (Select, Insert, Update, and Delete) for each interface table, and the Select operation for each interface view in Oracle E-Business Suite. By using these operations, you can perform the SELECT, INSERT, UPDATE, and DELETE statements qualified by a WHERE clause on the target interface table, and the SELECT statement qualified by a WHERE clause on the target interface view. These operations are also called data manipulation language (DML) operations.  
  
> [!IMPORTANT]
>  Before you can perform operations on interface tables and interface views, you must set the applications context for these artifacts in [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. This is because setting applications context facilitates secure transactions in Oracle E-Business Suite by setting user preferences (such as responsibility, organization, and language settings) and access control for an artifact. For more information about applications context and how to set it, see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  

## Supported DML operations  
 The following table shows the DML operations that the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports:  
  
|Operation|Description|  
|---------------|-----------------|  
|Select|Performs a Select Operation on the target interface table or interface view based on a supplied list of column names and a filter string that specifies a SQL WHERE clause.<br /><br /> The return value for a Select operation is a strongly-typed result set that contains the specified columns and rows.|  
|Insert|Performs an Insert operation on the target interface table. The Insert operation supports multiple-record insert into the target interface table based on a supplied record set.<br /><br /> The return value for an Insert operation is the number of rows inserted.<br /><br /> **InlineValue**<br /><br /> For all simple data records in an Insert operation, you can choose to override the value of a record by specifying a value for an optional attribute called **InlineValue**. The InlineValue attribute can be used to insert computed values into interface tables such as populating the primary key column using a sequence or inserting system date (using SYSDATE) into a date column. For example, in the following INSERT statement:<br /><br /> `<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/AR/AR_ARCHIVE_PURGE_INTERIM">   <RECORDSET>     <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/AR/AR_ARCHIVE_PURGE_INTERIM">       <TRNS_DATE InlineValue="sysdate">2008-06-21T15:52:19</TRNS_DATE>       <EMPNAME>John</EMPNAME>     </InsertRecord>   </RECORDSET>   </Insert>`<br /><br /> Even though “2008-06-21T15:52:19” is specified as a value for TRNS_DATE, the value of the **InlineValue** attribute, “SYSDATE,” (system date) will be inserted into the target interface table.<br /><br /> While using the InlineValue attribute:<br /><br /> - Avoid using constant values for the InlineValue attribute. For example, in the INSERT statement, if you specify `<EMPNAME InlineValue="John"/>` then it will result in an error. This is because the value of the InlineValue attribute is passed on as-is to Oracle, and in this case *John* is passed to Oracle E-Business Suite, which is not the expected value (expected value is *‘John’*). You would have to use single quotes around the employee name. For example: `<EMPNAME InlineValue="’John’"/>`.<br /><br /> - If you want to use a select query for the InlineValue attribute, you must enclose the SELECT statement in parentheses and also ensure that the select query fetches only a single record. For example: `<EMPNAME InlineValue="(SELECT NAME FROM MS_SAMPLE_EMPLOYEES WHERE ID=123)"/>`.<br /><br /> **Note:** If an element is marked as NOT NULL in Oracle E-Business Suite, you must specify a value for that element even if you have specified an inline value. Failing to do this will cause the schema validation to fail.|  
|Update|Performs an Update operation on the target interface table. The records to be updated are specified by a filter string that specifies a SQL WHERE clause. The values for the update are specified in a template record.<br /><br /> The return value for an Update operation is the number of rows updated.|  
|Delete|Performs a Delete operation on the target interface table based on a SQL WHERE clause that is specified in a filter string.<br /><br /> The return value for a Delete operation is the number of rows deleted.|  

## Important details  
- The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] surfaces the same set of standard operations (Select, Insert, Update, and Delete) for each table, and the Select operation for each view in the underlying Oracle database. The above DML operations are also valid for the underlying Oracle database tables and views.  

  - It is not required to set the applications context to perform operations on tables and views in the Oracle database. However, for custom Oracle E-Business Suite applications, users may or may not register the base database tables as interface tables. If a database table is not registered as an interface table, it is available under the **Tables** subnode in the **Artifact-Based View** node or in the **Schema Based View** node at design-time while using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
    These tables are associated with an Oracle E-Business application. So for any operation on these tables, you must set the application context. See Set Application Context[enter link description here](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## See also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)