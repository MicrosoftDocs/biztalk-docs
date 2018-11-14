---
title: Database Lookup Functoid
TOCTitle: Database Lookup Functoid
ms:assetid: 0f370a59-ec4d-4d93-9c8e-79716d86f297
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547392(v=BTS.80)
ms:contentKeyID: 51526259
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Database Lookup Functoid

 

Use the **Database Lookup** functoid ( ![](images/Aa562112.46f7eca0-1dba-456f-8720-24db8c35fae6(BTS.80).jpeg)) to extract a row from a database table as a Microsoft ActiveX Data Objects (ADO) recordset.

## Input

**Parameter 1:** A value for which to search in the specified database, table, and column.

**Parameter 2:** An ActiveX Data Objects .NET (ADO.NET) connection string for a compliant data source in which to search. ODBC data sources (including DSN sources) are not supported. You can reference an OLE DB Universal Data Link file to specify the connection string by using the **File Name** parameter to specify the full path and file name of the UDL file that contains the connection string information.


> [!NOTE]
> <P>Because of the overhead associated with parsing a UDL file, we recommend a connection string that does not reference a UDL. As an alternative, build a helper library that returns an appropriate connection string when called by the Scripting functoid.</P>




> [!NOTE]
> <P>We recommend that you verify that the target data source meet the performance goals for the BizTalk Server solution.</P>



**Parameter 3:** The name of the table in the database in which to search.

**Parameter 4:** The name of the column in the table in which to search.

## Output

**Output 1:** An ADO.NET recordset that contains the value sought. Regardless of the number of rows that match the specified value, only the first matching row is included in the recordset.

## Remarks

Use this functoid in conjunction with the [Value Extractor](value-extractor-functoid.md) and [Error Return](error-return-functoid.md) functoids.


> [!IMPORTANT]
> <P>To avoid the security risks associated with your Microsoft SQL Server password being visible as part of the connection string you provide as input parameter 2 or through a UDL file, we recommend using Windows NT authentication instead of SQL Server authentication.</P>



## Best Practices

Hard-coding the SQL connection strings might lead to maintenance overhead and serviceability issues. To avoid these, you can externally configure data sources in the Database Lookup functoid. You can get the SQL connection string (parameter 2) from a scripting functoid, which can then be linked to the Database Lookup functoid.

In the following figure, you can see that the second parameter to the Database Lookup functoid is passed through a script present in the scripting functoid.

![Database Lookup Functoid](images/Aa547392.6107a7d9-d93d-49ec-a383-5db7a418acd7(BTS.80).jpeg "Database Lookup Functoid")

You can use the following scripts in the Scripting functoid.

``` 
public string connectionString1()  
        {  
            string serverName = Environment.MachineName;  
            string connectionString1 = string.Format("Data Source = {0}; Initial Catalog = myDataBase; Integrated Security = SSPI;", serverName);  
            return connectionString1;  
        }  
  
```

``` 
public string connectionString2(string password)  
        {  
            string serverName = Environment.MachineName;  
            string userdomain = Environment.UserDomainName;  
            string userName = Environment.UserName;  
            string connectionString2 = string.Format(@"Data Source={0};Initial Catalog=myDataBase;Integrated Security=SSPI;User ID={1}\{2};Password={3};", serverName, userdomain, userName, password);  
            return connectionString2;  
        }  
  
```

## See Also

[Database Functoids Reference](database-functoids-reference.md)  
[Database Functoids](https://msdn.microsoft.com/library/aa560892\(v=bts.80\))  
[How to Add Basic Functoids to a Map](https://msdn.microsoft.com/library/aa560635\(v=bts.80\))

