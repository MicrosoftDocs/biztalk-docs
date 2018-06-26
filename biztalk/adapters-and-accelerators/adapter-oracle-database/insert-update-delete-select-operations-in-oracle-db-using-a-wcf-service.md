---
title: "Insert, update, delete, or select operations in Oracle Database using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model, Delete operation"
  - "WCF service model, Select operation"
  - "WCF service model, Insert operation"
  - "WCF service model, Update operation"
ms.assetid: d1a9f44f-ea0b-4dd6-9489-fa0d963848c4
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Insert, update, delete, or select operations in Oracle Database using the WCF Service Model
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces a set of basic Insert, Update, Delete, and Select operations on Oracle database tables and views. By using these operations, you can perform simple SQL INSERT, UPDATE, SELECT, and DELETE statements qualified by a WHERE clause on a target table or view. To perform more complex operations, for example a SQL SELECT query that uses the JOIN operator, you can use the SQLEXECUTE operation. For more information about the SQLEXECUTE operation, see [Performing a SQLEXECUTE Operation in Oracle Database Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).  
  
 The following table summarizes the basic SQL operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces on tables and views. For a complete description of these operations, see [Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).  
  
|Operation|Description|  
|---------------|-----------------|  
|Insert|The Insert operation supports multiple record or bulk inserts into the target table or view:<br /><br /> -   A multiple record Insert operation inserts rows into a table or view based on a supplied record set.<br />-   A bulk Insert operation inserts rows into a table or view based on a supplied SQL SELECT query and column list. The records that the query returns are inserted into the target table based on the column list.|  
|Select|Performs a SQL SELECT query on the target table based on a supplied list of column names and a filter string that specifies a SQL WHERE clause.|  
|Update|Performs an UPDATE on the target table. The records to be updated are specified by a filter string that specifies a SQL WHERE clause. The values for the update are specified in a template record.|  
|Delete|Performs a DELETE on the target table based on a SQL WHERE clause that is specified in a filter string.|  
  
## About the Examples Used in this Topic  
 The examples in this topic use the /SCOTT/ACCOUNTACTIVITY table. A script to generate this table is supplied with the SDK samples. For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).  
  
## The WCF Client Class  
 The name of the WCF client generated for the basic SQL operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces is based on the name of the table or view, as in the following table.  
  
|Oracle Database Artifact|WCF Client Name|  
|------------------------------|---------------------|  
|Table|[SCHEMA]Table[TABLE_NAME]Client|  
|View|[SCHEMA]View[VIEW_NAME]Client|  
  
 [SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.  
  
 [TABLE_NAME] = The name of the table; for example, ACCOUNTACTIVITY.  
  
 [VIEW_NAME] = The name of the view.  
  
 The following table shows the method signatures for the basic SQL operations on a table. The signatures are the same for a view, except that the view namespace and name replace those of the table.  
  
|Operation|Method Signature|  
|---------------|----------------------|  
|Insert|long Insert([TABLE_NS].[TABLE_NAME]RECORDINSERT[] RECORDSET, string COLUMN_NAMES, string QUERY);|  
|Select|[TABLE_NS].[TABLE_NAME]RECORDSELECT[] Select(string COLUMN_NAMES, string FILTER);|  
|Update|long Update([TABLE_NS].[TABLE_NAME]RECORDUPDATE RECORDSET, string FILTER);|  
|Delete|Long Delete(string FILTER);|  
  
 [TABLE_NS] = The name of the table namespace; for example, microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.  
  
 [TABLE_NAME] = The name of the table; for example, ACCOUNTACTIVITY.  
  
 The record types used by the Insert, Update, and Select operations are all defined in the table or view namespace.  
  
 The following code shows the method signatures for a WCF client class generated for the Delete, Insert, Select and Update operations on the /SCOTT/ACCOUNTACTIVITY table.  
  
```  
public partial class SCOTTTableACCOUNTACTIVITYClient : System.ServiceModel.ClientBase<SCOTTTableACCOUNTACTIVITY>, SCOTTTableACCOUNTACTIVITY {  
  
    public long Delete(string FILTER);  
  
    public long Insert(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] RECORDSET, string COLUMN_NAMES, string QUERY);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] Select(string COLUMN_NAMES, string FILTER);  
  
    public long Update(microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE RECORDSET, string FILTER);  
}  
```  
  
## Invoking the Basic SQL Operations  
 To invoke the basic SQL operations on a table or view by using a WCF client, perform the following steps.  
  
1. Generate a WCF client class for the target table or view. This class should contain methods for the operations that you will invoke on the target artifact.  
  
2. Create an instance of the WCF client class and invoke its methods to perform operations on the table or view.  
  
   For more detailed information about how to create a WCF client class and invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Overview of the WCF Service Model with the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md).  
  
   The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] executes each operation inside of a transaction on the Oracle database. You can control the isolation level of this transaction by setting the **TransactionIsolationLevel** binding property. For more information about the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties, see [Working with BizTalk Adapter for Oracle Database Binding Properties](https://msdn.microsoft.com/library/dd788467.aspx).  
  
   The following sections provide details about how to invoke each basic SQL operation in your code.  
  
###  <a name="BKMK_InsertOperation"></a> Insert Operation  
 The following table shows how to set parameters for multiple record Insert and bulk Insert operations.  
  
|Insert operation type|RECORDSET|COLUMN_NAMES|QUERY|  
|---------------------------|---------------|-------------------|-----------|  
|Multiple record|A collection of INSERTRECORDS that should be inserted into the target.|null|null|  
|Bulk|null|A comma-delimited list of column names in the target; for example, "TID, ACCOUNT". The column list specifies the columns into which the query results should be placed in each inserted row. The query must return a result set that matches the columns specified in the column list in both number and type.|A SQL SELECT query on a database table or view that returns a result set to insert into the target; for example, "SELECT (TID, ACCOUNT) FROM NEW_TRANSACTIONS WHERE ACCOUNT = 100001". The result set must match the column list in both number and type.|  
  
 The Insert operation returns the number of records inserted into the target.  
  
> [!IMPORTANT]
>  In the WCF service model, the record set used in the Insert operation is strongly-typed. You can set the value of a nillable column to **null** in a record to exclude that column from the Insert operation; however, you cannot set the value of a non-nillable column to **null**. This means that in a multiple record Insert operation, you must supply values for all non-nillable columns in each record. In addition, there is no streaming support for the basic SQL operations when you use the WCF service model. If your multiple record Insert operation involves a large record set, this may be an important consideration. For more information, see [Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model](#BKMK_LimitationsInvoking).  
  
 The following code shows a multiple record Insert operation (two records) that targets the ACCOUNTACTIVITY table.  
  
```  
// Insert records  
                using (SCOTTTableACCOUNTACTIVITYClient aaTableClient =   
                    new SCOTTTableACCOUNTACTIVITYClient("OracleDBBinding_SCOTT.Table.ACCOUNTACTIVITY"))  
                {  
                    long recsInserted;  
  
                    aaTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
                    aaTableClient.ClientCredentials.UserName.Password = "TIGER";  
  
                    try  
                    {  
                        aaTableClient.Open();  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    // Do a multiple record Insert of 2 records for account 100001  
  
                    microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[] insertRecs =  
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT[2];  
  
                                  TID__COMPLEX_TYPE tid = new TID__COMPLEX_TYPE();  
                                  tid.InlineValue = "tidSequence.NextVal()";  
  
                                  ACCOUNT__COMPLEX_TYPE account = new ACCOUNT__COMPLEX_TYPE();  
                                  account.Value = 100001;  
  
                    AMOUNT__COMPLEX_TYPE amount = new AMOUNT__COMPLEX_TYPE();  
                    amount.Value = 400;  
  
                    TRANSDATE__COMPLEX_TYPE transdate = new TRANSDATE__COMPLEX_TYPE();  
                    transdate.Value = DateTime.Now.Date;  
  
                    PROCESSED__COMPLEX_TYPE processed = new PROCESSED__COMPLEX_TYPE();  
                    processed.Value = "n";  
  
                    DESCRIPTION__COMPLEX_TYPE description1 = new DESCRIPTION__COMPLEX_TYPE();  
                    description1.Value = "Inserted Record #1";  
  
                    DESCRIPTION__COMPLEX_TYPE description2 = new DESCRIPTION__COMPLEX_TYPE();  
                    description2.Value = "Inserted Record #2";  
  
                    insertRecs[0] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[0].TID = tid;  
                    insertRecs[0].ACCOUNT = account;  
                    insertRecs[0].AMOUNT = amount;  
                    insertRecs[0].TRANSDATE = transdate;  
                    insertRecs[0].DESCRIPTION = description1;  
                    insertRecs[0].PROCESSED = processed;  
  
                    insertRecs[1] =   
                        new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDINSERT();  
                    insertRecs[1].TID = tid;  
                    insertRecs[1].ACCOUNT = account;  
                    insertRecs[1].AMOUNT = amount;  
                    insertRecs[1].TRANSDATE = transdate;  
                    insertRecs[1].DESCRIPTION = description2;  
                    insertRecs[1].PROCESSED = processed;  
  
                    try  
                    {  
                        recsInserted = aaTableClient.Insert(insertRecs, null, null);  
                    }  
                    catch (Exception ex)  
                    {  
                        // handle exception  
                        Console.WriteLine("Exception: " + ex.Message);  
                        throw;  
                    }  
  
                    Console.WriteLine("Insert Done: {0} records inserted", recsInserted);  
```  
  
### Select Operation  
 The following table shows the parameters for the Select operation.  
  
|COLUMN_NAMES|FILTER|  
|-------------------|------------|  
|A comma-delimited list of column names in the target; for example, "TID, ACCOUNT". The column list specifies the columns of the target that should be returned in the result set. Columns not specified in the column list will be set to their .NET default values in the returned record set. For nillable columns, this value is **null**.|The contents of a SQL WHERE clause that specifies the target rows of the query; for example, "DESCRIPTION = 'Insert Record #1'". You can set this parameter to **null** to return all rows of the target.|  
  
 The Select operation returns a strongly-typed record set based on the row type of the target.  
  
> [!IMPORTANT]
>  There is no streaming support for the basic SQL operations when you use the WCF service model. If your query returns a large record set, you might be able to improve performance by using the WCF channel model. For more information, see [Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model](#BKMK_LimitationsInvoking).  
  
 The following code shows a Select operation that targets the ACCOUNTACTIVITY table. The returned records are written to the console.  
  
```  
// Declare a variable to hold the result set  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
  
// Select all records and write them to the console  
try  
{  
    selectRecords = aaTableClient.Select("*", null);  
}  
catch (Exception ex)  
{  
    // handle exception  
}  
  
Console.WriteLine("ACCOUNTACTIVITY before any operations");  
for (int i = 0; i \< selectRecords.Length; i++)  
{  
    Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", selectRecords[i].TID,  
    selectRecords[i].ACCOUNT,  
    selectRecords[i].AMOUNT,  
    selectRecords[i].TRANSDATE,  
    selectRecords[i].DESCRIPTION);  
}  
```  
  
> [!NOTE]
>  This code omits steps to create, configure, and open the WCF client instance. For an example that includes these steps, see [Insert Operation](#BKMK_InsertOperation).  
  
### Update Operation  
 The following table shows the parameters for the Update operation.  
  
|RECORDSET|FILTER|  
|---------------|------------|  
|A strongly-typed template record based on the row type of the target. The template record specifies the update values for the target rows. For nillable row columns, you can specify a null value to indicate that the column should not be updated in the target rows.|The contents of a SQL WHERE clause that specifies the rows to be updated in the target. For example, "DESCRIPTION= 'Inserted Record #1'".|  
  
 The Update operation returns the number of rows deleted from the target.  
  
> [!IMPORTANT]
>  In the WCF service model, the template record used in the Update operation is strongly-typed. If a column is nillable, you can omit the column from the Update operation by setting its value to **null** in the template record; however, if a column is not nillable, then you must set its value in the template record. For example, if a column is a primary key, it must contain a value. For more information, see [Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model](#BKMK_LimitationsInvoking).  
  
 The following code shows an Update operation that targets the ACCOUNTACTIVITY table.  
  
```  
long recsUpdated;  
  
...  
  
// Create updated template. The TID, TIME, AMOUNT, and DESCRIPTION fields will be updated  
microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE updateRecord =  
    new microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDUPDATE();  
        updateRecord.TID = tidSequence.NextVal();  
        updateRecord.ACCOUNT = null;  
        updateRecord.AMOUNT = 300;  
        updateRecord.TRANSDATE = DateTime.Now.Date;  
        updateRecord.DESCRIPTION = "Updated Record #2";  
        updateRecord.PROCESSED = null;  
  
// Set filter string to specify the target record by using the DESCRIPTION field  
string filter = "DESCRIPTION = 'Inserted Record #2'";  
  
try  
{  
    recsUpdated = aaTableClient.Update(updateRecord, filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
    ...  
}  
  
Console.WriteLine("{0} records updated", recsUpdated);  
```  
  
> [!NOTE]
>  This code omits steps to create, configure, and open the WCF client instance. For an example that includes these steps, see [Insert Operation](#BKMK_InsertOperation).  
  
### Delete Operation  
 The following table shows the parameters for the Delete operation.  
  
|FILTER|  
|------------|  
|The contents of a SQL WHERE clause that specifies the rows to be deleted from the target. For example, "DESCRIPTION= 'Inserted Record #1'".|  
  
 The Delete operation returns the number of rows deleted from the target. The following code shows a Delete operation that targets the ACCOUNTACTIVITY table.  
  
```  
// Set filter string equal to the DESCRIPTION field of the target record  
string filter = "DESCRIPTION = 'Inserted Record #1'";  
  
try  
{  
    recsDeleted = aaTableClient.Delete(filter);  
}  
catch (Exception ex)  
{  
    // handle exception  
  
    ...  
}  
Console.WriteLine("{0} records deleted", recsDeleted);  
```  
  
> [!NOTE]
>  This code omits steps to create, configure, and open the WCF client instance. For an example that includes these steps, see the [Insert Operation](#BKMK_InsertOperation).  
  
##  <a name="BKMK_LimitationsInvoking"></a> Limitations of Invoking the Basic SQL Operations by Using the WCF Service Model  
 The following limitations exist when you invoke the basic SQL operations by using a WCF client:  
  
- **Insert operation.** The record set used in a multiple record Insert operation is strongly-typed and therefore includes all row columns. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a null value in a record to mean that the column should be excluded from the Insert operation; however, non-nillable columns cannot be excluded because you cannot set them to a null value. Therefore, you must specify values for non-nillable columns when you perform a multiple record Insert operation.  
  
- **Insert operation.** The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a **DbNull** value in a nillable data column to mean that the column should be excluded from a multiple record Insert operation. This means that you cannot set a nillable column to **DbNull** on the Oracle database in a multiple record Insert operation.  
  
- **Insert operation.** There is no streaming support for multiple record insert operations that involve a large record set.  
  
- **Update operation.** The template record used in an Update operation is strongly-typed and therefore includes all row columns. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a null value in this record to mean that the column should be excluded from the Update operation; however, non-nillable columns cannot be excluded because you cannot them to a null value. Therefore, you must specify values for non-nillable columns when you perform an Update operation.  
  
- **Update operation.** The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] interprets a **DbNull** value in a nillable data column in the template record to mean that the column should be excluded from the operation. This means that you cannot set a nillable column to **DbNull** on the Oracle database by using the Update operation.  
  
- **Select operation.** There is no streaming support for SELECT queries that return a large record set.  
  
  For scenarios where these limitations present challenges, you can invoke the operation by using the WCF channel model because:  
  
- By using the WCF channel model, you can exclude specific data columns from Update and Insert operations.  
  
- The WCF channel model provides node-level streaming support for the basic SQL operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes.  
  
  For more information about using the WCF channel model with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Develop Oracle Database Applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).  
  
## See Also  
 [Develop Oracle Database Applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)