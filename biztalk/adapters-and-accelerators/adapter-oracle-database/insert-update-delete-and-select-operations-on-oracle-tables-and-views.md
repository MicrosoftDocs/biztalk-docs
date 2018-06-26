---
title: "Insert, Update, Delete, and Select operations on Oracle tables and views | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "operations, on tables and views"
  - "operations, performing"
  - "data manipulation language"
  - "Delete operation"
  - "Insert operation"
  - "Update operation"
  - "DELETE statement"
  - "DML operation"
  - "Select operation"
  - "INSERT statement"
  - "UPDATE statement"
ms.assetid: af65fac4-3c16-40c4-ae7a-9c1757223f99
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Insert, Update, Delete, and Select operations on Oracle tables and views
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces a set of standard operations on each Oracle database table and view. By using these operations, you can perform simple SQL INSERT, UPDATE, SELECT, and DELETE statements qualified by a WHERE clause on the target table (or view). These operations are also called data manipulation language (DML) operations. To perform more complex operations, for example a SQL SELECT query that uses the JOIN operator, you can use the SQLEXECUTE operation. For more information about the SQLEXECUTE operation, see [SQLEXECUTE Operation in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/sqlexecute-operation-in-oracle-database.md).  
  
 The following table shows the DML operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports:  
  
|Operation|Description|  
|---------------|-----------------|  
|Insert|Performs an Insert operation on the target table or view. The Insert operation supports multiple record or bulk inserts into the target table or view:<br /><br /> - A multiple record Insert operation inserts rows into a table or view based on a supplied record set.<br /><br /> - A bulk Insert operation inserts rows into a table or view based on a supplied SQL SELECT query and column list. The records that the query returns are inserted into the target table based on the column list.<br /><br /> The return value for an Insert operation is the number of rows inserted.<br /><br /> **Note:** Both multiple-record insert and bulk insert cannot be combined in the same message.<br /><br /> **InlineValue**<br /><br /> For all simple data records in a multiple record Insert operation, you can choose to override the value of a record by specifying a value for an optional attribute called **InlineValue**. The InlineValue attribute can be used to insert computed values into tables or views such as populating the primary key column using a sequence or inserting system date (using SYSDATE) into a date column. For example, in the following INSERT statement:<br /><br /> `<Insert xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY">   <RECORDSET>     <ACCOUNTACTIVITYRECORDINSERT>       <ACCOUNT>10001</ACCOUNT>       <EMPNAME>John</EMPNAME>       <AMOUNT>1500</AMOUNT>       <TRANSDATE InlineValue="SYSDATE">2008-06-21T15:52:19</TRANSDATE>       </ACCOUNTACTIVITYRECORDINSERT >   </RECORDSET> </Insert>`<br /><br /> Even though “2008-06-21T15:52:19” is specified as a value for the TRANSDATE column, the value of the InlineValue attribute, “SYSDATE,” (system date) will be inserted into the target table.<br /><br /> While using the InlineValue attribute:<br /><br /> - Avoid using constant values for the InlineValue attribute. For example, in the INSERT statement, if you specify `<EMPNAME InlineValue="John"/>` then it will result in an error. This is because the value of the InlineValue attribute is passed on as-is to Oracle, and in this case *John* is passed to the Oracle database, which is not the expected value (expected value is *‘John’*). You would have to use single quotes around the employee name. For example: `<EMPNAME InlineValue="’John’"/>`.<br /><br /> - If you want to use a select query for the InlineValue attribute, you must enclose the SELECT statement in parentheses and also ensure that the select query fetches only a single record. For example: `<EMPNAME InlineValue="(SELECT NAME FROM MS_SAMPLE_EMPLOYEES WHERE ID=123)"/>`.<br /><br /> **Note:** If an element is marked as NOT NULL in the Oracle database, you must specify a value for that element even if you have specified an inline value. Failing to do this will cause the schema validation to fail.|  
|Select|Performs a SQL SELECT query on the target table or view based on a supplied list of column names and a filter string that specifies a SQL WHERE clause.<br /><br /> The return value for a Select operation is a strongly-typed result set that contains the specified columns and rows.|  
|Update|Performs an Update operation on the target table or view. The records to be updated are specified by a filter string that specifies a SQL WHERE clause. The values for the update are specified in a template record.<br /><br /> The return value for an Update operation is the number of rows updated.|  
|Delete|Performs a Delete operation on the target table or view based on a SQL WHERE clause that is specified in a filter string.<br /><br /> The return value for a Delete operation is the number of rows deleted.|  
  
 For more information about:  
  
- Performing these operations using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Insert, Update, Delete, and Select Operations by Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-using-biztalk-server-with-oracle-db.md).  
  
- Performing these operations using the WCF service model, see [Insert, Update, Delete, and Select Operations by Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md).  
  
- Performing these operations using the WCF channel model, see [Run an Insert Operation in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md).  
  
- Message structures and SOAP action for performing DML operations, see [Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)