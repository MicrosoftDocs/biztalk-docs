---
title: "Connect with an MsDb2Connection | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b5f936c-a0cf-47aa-adc0-2130a74ac7d2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect with an MsDb2Connection
The first step in accessing a remote DB2 database is to connect to the database. You must use `Microsoft.HostIntegration.MsDb2Client.MsDb2Connection` to access an IBM DB2 data source. After you have connected, you can retrieve, modify, and update any information that you want. Note that connections are not implicitly released when the MsDb2Connection falls out of scope or is reclaimed by garbage collection. Therefore, you must close the connection when you are finished using it. You can close a connection by using either `MsDb2Connection.Close` or `MsDb2Connection.Dispose`.  
  
## Example  
 The following example demonstrates how to connect to a DB2 database.  
  
```  
Public void SampleConnect()  
{  
   MsDb2Connection myConnection = null;  
   Try  
   {  
      myConnection = new MsDb2Connection(@"file name=HOST.udl ");  
      myConnection.Open();  
      // Perform any necessary tasks here.  
      myConnection.Close();  
   }  
finally  
   {  
      if(myConnection!= null)  
         myConnection.Dispose();  
   }  
}  
```  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db21.md)   
 [How to Connect to and Disconnect from a Host File System](../core/how-to-connect-to-and-disconnect-from-a-host-file-system2.md)