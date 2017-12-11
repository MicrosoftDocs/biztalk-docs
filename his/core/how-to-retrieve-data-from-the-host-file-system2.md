---
title: "How to Retrieve Data from the Host File System2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 011f814a-bd2a-42f4-8050-4591f23fb3da
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Retrieve Data from the Host File System
Just as you can do with other managed data providers, you can access host data with an implementation of a `DataReader` object through `HostfileCommand`.  
  
### To retrieve data using a data reader  
  
1.  Create an instance of `HostFileCommand`.  
  
2.  Create a `DataReader` object through a call to `HostFileCommand.ExecuteDBDataReader`.  
  
     Calling `ExecuteDBDataReader` retrieves data rows from the data source.  
  
3.  Use `DBDataReader.Read` to obtain a row from the results of the query.  
  
     You can access each column of the returned row by passing the name or ordinal reference of the column to the `DBDataReader` object. However, for best performance, the `DBDataReader` object provides a series of methods that enable you to access column values in their native data types (`GetDateTime`, `GetDouble`, `GetGuid`, `GetInt32`, and so on).  
  
4.  Once you are finished with the `DBDataReader` object, call `DBDataReader.Close`.  
  
     If your `HostFileCommand` object contains output parameters or return values, they will not be available until the `DBDataReader` is closed.  
  
     Note that while `DBDataReader` is open, the `HostFileConnection` is in use exclusively by that `DBDataReader`. You cannot execute any commands for the `HostFileConnection`, including creating another `DBDataReader`, until the original `DBDataReader` is closed.  
  
## See Also  
 [Retrieving Information from the Host File System](../core/retrieving-information-from-the-host-file-system2.md)   
 [BizTalk Adapter for Host Files Configuration](../HIS2010/biztalk-adapter-for-host-files-configuration2.md)