---
title: "How to Create a Connection String for a .udl File2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd343068-288a-4b30-b7c1-410ed1a38cc5
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Create a Connection String for a .udl File
A universal data link (.udl) file is essentially a text file that contains the connection string for an OLE DB data source. You can create a .udl file by using the appropriate `DB2OleDbConnectionString` or `FileSysOleDbConnectionString` constructor, and then save the string to secondary storage with a call to `Save`. The Data Access Library automatically creates the appropriate .udl file to store the string in, and save the file to disk.  
  
### To create a .udl file and associated connection string  
  
1.  Create an empty connection string by calling a connection string constructor.  
  
     Calling the constructor creates a connection string with default settings. These default settings can be set only through the Data Access Tool user interface.  
  
     If you use a file path for a file that currently exists, the system loads the connection string information in that file instead.  
  
     You can determine the default path your system uses for storing .udl files with a call to `DataAccessSettings.MakeUDLPath`. `DataAccessSettings` also stores the default paths for DSN and HCD files.  
  
2.  Add in the relevant connection information to the connection string by calling the various connection string properties, such as `DataSourceName`, `UserName`, or `Password`.  
  
     You can also retrieve the full connection string as a text string with a call to `GetString`, and then save the modified string with `SetString`.  
  
3.  Save the string by calling the relevant `Save` method, such as `DB2OleDbConnectionString.Save`.  
  
     The system saves the connection string in a .udl file. The system creates the .udl file using the file path passed in the `name` parameter of the constructor. If the file does not contain the full path, the system uses the default path as described in `DataAccessSettings.UDLpath`.  
  
 The following code example demonstrates how to create a .udl file using a new file name, user name, and password.  
  
```  
static DB2OleDbConnectionString CreateUDLFile(string FileName, string NameOfUser, string PassWord, ref System.Exception myException)  
{  
   try  
   {  
      DB2OleDbConnectionString myConnection = new DB2OleDbConnectionString(FileName, false);  
      myConnection.UserName = NameOfUser;  
      myConnection.Password = PassWord;  
      myConnection.Save();  
      System.Exception MyEx= new System.Exception(@"Successful Creation", null);  
      myException = MyEx;  
      return myConnection;  
  
   }  
   catch (Exception ex)  
   {  
      myException = ex;  
      return null;  
   }  
}  
```  
  
## See Also  
 [How to Retrieve Data](../core/how-to-retrieve-data.md)   
 [How to Edit a Configuration &#91;bpi&#93; &#91;HIS09_R2&#93;](http://msdn.microsoft.com/en-us/c863170f-e384-4962-afa4-15bf06cf6186)   
 [Data Access Library Tasks](../core/data-access-library-tasks.md)