---
title: "How to Connect with an MsDb2Connection1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2bc1c02-1e36-4dff-9f35-5e3b27199ad7
caps.latest.revision: 3
---
# How to Connect with an MsDb2Connection
The first step in accessing a remote DB2 database is to connect to the database. You must use <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Connection> to access an IBM DB2 data source. After you have connected, you can retrieve, modify, and update any information that you want. Note that connections are not implicitly released when the MsDb2Connection falls out of scope or is reclaimed by garbage collection. Therefore, you must close the connection when you are finished using it. You can close a connection by using either `MsDb2Connection.Close` or `MsDb2Connection.Dispose`.  
  
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
 [Working with the Managed Provider for DB2](../HIS2010/working-with-the-managed-provider-for-db22.md)   
 [How to Connect to and Disconnect from a Host File System](../HIS2010/how-to-connect-to-and-disconnect-from-a-host-file-system1.md)