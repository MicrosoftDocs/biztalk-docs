---
title: "Reading Data from a Database1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc3a5b72-9e9b-4656-bc01-7889c2c9892b
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Reading Data from a Database
You can use <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> to retrieve a read-only, forward-only stream of data from a database. Using <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> can increase application performance and reduce system overhead because only one row at a time is ever in memory.  
  
 After you create an instance of the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command> object, you can create an <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> by calling <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteReader%2A> to retrieve rows from a data source.  
  
 You can use <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader.Read%2A?displayProperty=fullName> to obtain a row from the results of the query. You access each column of the returned row by passing the name or ordinal reference of the column to <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader>. However, for best performance, <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> provides a series of methods that enable you to access column values in their native data types. Using the typed accessor methods when the underlying data type is known reduces the amount of type conversion required when retrieving the column value.  
  
 <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> also provides a nonbuffered stream of data that enables procedural logic to efficiently process results from a data source sequentially. <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> is a good choice when you are retrieving large amounts of data because the data is not cached in memory.  
  
 After you are finished with <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader>, be sure to call the `Close` method. In addition, output parameters and return values from an <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command> are not available until <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2DataReader> is closed.  
  
> [!NOTE]
>  The Distributed Relational Data Architecture (DRDA) uses a "." as a decimal point and a "," to separate numerical values. If you are working in a language, such as German, that uses a "," as a decimal point, you might receive an error when you are retrieving data from your database. To avoid this error, use `System.Globalization.CultureInfo.InvariantCulture` when you call the `ToString` and `Parse` methods.  
  
## Example  
 The following example shows how to read data from a DB2 database by reading a row from a `SELECT` statement:  
  
```  
Public void ReadMyData(string myConnString)   
{  
   string mySelectQuery = "SELECT OrderID, CustomerID FROM Orders";  
   MsDb2Connection myConnection = new MsDb2Connection(myConnString);  
   MsDb2Command myCommand = new MsDb2Command(mySelectQuery,myConnection);  
   myConnection.Open();  
   MsDb2DataReader myReader;  
   myReader = myCommand.ExecuteReader();  
   // Always call Read before accessing data.  
   While (myReader.Read())  
   {  
       Console.WriteLine(myReader.GetInt32(0) + ", "  
       + myReader.GetString(1));  
   }  
   // Always close when done reading.  
   myReader.Close();  
   // Close the connection when done.  
   myConnection.Close();  
}  
  
```  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db2.md)   
 [Managed Provider for DB2 Programmer's Guide](../core/managed-provider-for-db2-programmer-s-guide.md)   
 [Managed Provider for DB2 Programmer's Reference &#91;bpi&#93; &#91;HIS09_R2&#93;](http://msdn.microsoft.com/en-us/a50e991f-d651-40cb-a45c-d64fa132d251)