---
description: "Learn more about: How to Obtain a Single Value from a DB2 Database"
title: "How to Obtain a Single Value from a DB2 Database1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Obtain a Single Value from a DB2 Database
You might need to return database information that is just a single value rather than in the form of a table or data stream. For example, you might want to return the result of an aggregate function such as Count(*), Sum(Price), or Avg(Quantity). The `Command` object enables you to return single values by using the `ExecuteScalar` method. The `ExecuteScalar` method returns as a scalar value the value of the first column of the first row of the result set.  
  
## Example  
 The following code example demonstrates how to retrieve a single value from a DB2 database.  
  
```  
static void SingleValueConnection()  
{  
    MsDb2Connection myConnection = null;  
    try  
    {  
// Obtaining a single value as a database.  
        myConnection = new MsDb2Connection(@"file name=HOST.udl ");  
        myConnection.Open();  
        MsDb2Command myCommand = new MsDb2Command("SELECT Count(*) FROM Orders", myConnection);  
       Int32 count = (Int32)myCommand.ExecuteScalar();  
        myConnection.Close();  
    }  
        catch (Exception exc)  
    {  
        Console.WriteLine(exc);  
        Console.ReadLine();  
    }  
  
    finally  
    {  
        if(myConnection!= null)  
            myConnection.Dispose();  
    }  
} // End SingleValueConnection.  
  
```  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db21.md)
