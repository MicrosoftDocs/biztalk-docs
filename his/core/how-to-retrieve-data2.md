---
title: "Retrieve Data | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a990a46f-86ea-4348-8151-286248c92de7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Retrieve Data
Creating connection string information requires that you create an object that is derived from the `IConnectionString` class, such as `DB2OdbcConnectionString` or `DB2OleDbConnectionString`. After you create the string, you can save, modify, or retrieve information from it by using the associated properties.  
  
## Retrieve and modify connection string information  
  
1. Create a new connection string by calling the specific type of connection string constructor, using the file path of the .udl file that contains the specified connection string.  
  
    Or, you can call `ReadUDL` for the specified `ConnectionString` type. Many of the `ConnectionString` classes also have a `Clone` method that you may want to use. Note that `Clone` does not load the current instance into active memory, but instead makes a copy that you can later modify and save to disk.  
  
    If you are attempting to retrieve data from a connection string that you currently have an instance of, you can call `Load`. For example, if you recently created a new connection string and called `Save`, you can retrieve the object from storage and into active memory by calling `Load` on the object again.  
  
    If you use a path that describes a file that does not exist, the system creates a .udl new file using the path described.  
  
2. Retrieve the connection data from your current instance by using `GetString` or by accessing the relevant property.  
  
    Using `GetString` enables you to manipulate the connection string as though it were a standard text string. In contrast, accessing the value as a property is usually simpler and safer.  
  
3. When you are finished viewing or manipulating the relevant value, return the value to the object by calling `SetString` or by setting the appropriate property.  
  
4. When you are finished, save your changes to secondary storage by calling `Save`.  
  
   The following code example demonstrates how to retrieve, change, and save connection string data.  
  
```  
static System.Exception ChangeCommentInUDL(string connString, string newComment)  
{  
   try  
   {  
      IConnectionString udl = DB2OleDbConnectionString.ReadUDL(connString);  
      udl.Comment = newComment;  
      udl.Save();  
      System.Exception noException = null;  
      return noException;  
  
   }  
   catch (System.Exception ex)  
   {  
      return ex;  
   }  
}  
```  
  
## See Also  
 [Creating a Connection String](../core/creating-a-connection-string1.md)   