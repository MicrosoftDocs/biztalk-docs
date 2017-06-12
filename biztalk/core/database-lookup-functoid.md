---
title: "Database Lookup Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Database Lookup functoids"
ms.assetid: 0f370a59-ec4d-4d93-9c8e-79716d86f297
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Database Lookup Functoid
Use the **Database Lookup** functoid ( ![](../core/media/dblookup.gif "dblookup")) to extract a row from a database table as a Microsoft ActiveX Data Objects (ADO) recordset.  
  
## Input  
 **Parameter 1:** A value for which to search in the specified database, table, and column.  
  
 **Parameter 2:** An ActiveX Data Objects .NET (ADO.NET) connection string for a compliant data source in which to search.  ODBC data sources (including DSN sources) are not supported. You can reference an OLE DB Universal Data Link file to specify the connection string by using the **File Name** parameter to specify the full path and file name of the UDL file that contains the connection string information.  
  
> [!NOTE]
>  Because of the overhead associated with parsing a UDL file, we recommend a connection string that does not reference a UDL.  As an alternative, build a helper library that returns an appropriate connection string when called by the Scripting functoid.  
  
> [!NOTE]
>  We recommend that you verify that the target data source meet the performance goals for the BizTalk Server solution.  
  
 **Parameter 3:** The name of the table in the database in which to search.  
  
 **Parameter 4:** The name of the column in the table in which to search.  
  
## Output  
 **Output 1:** An ADO.NET recordset that contains the value sought. Regardless of the number of rows that match the specified value, only the first matching row is included in the recordset.  
  
## Remarks  
 Use this functoid in conjunction with the [Value Extractor](../core/value-extractor-functoid.md) and [Error Return](../core/error-return-functoid.md) functoids.  
  
> [!IMPORTANT]
>  To avoid the security risks associated with your Microsoft SQL Server password being visible as part of the connection string you provide as input parameter 2 or through a UDL file, we recommend using Windows NT authentication instead of SQL Server authentication.  
  
## Best Practices  
 Hard-coding the SQL connection strings might lead to maintenance overhead and serviceability issues. To avoid these, you can externally configure data sources in the Database Lookup functoid. You can get the SQL connection string (parameter 2) from a scripting functoid, which can then be linked to the Database Lookup functoid.  
  
 In the following figure, you can see that the second parameter to the Database Lookup functoid is passed through a script present in the scripting functoid.  
  
 ![Database Lookup Functoid](../core/media/scripting-databasefunctoid.gif "Scripting_DatabaseFunctoid")  
  
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
 [Database Functoids Reference](../core/database-functoids-reference.md)   
 [Database Functoids](../core/database-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)