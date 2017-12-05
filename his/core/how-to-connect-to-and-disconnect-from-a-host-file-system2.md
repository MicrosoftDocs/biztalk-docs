---
title: "How to Connect to and Disconnect from a Host File System2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2398fce4-22e2-46c4-a789-2eec3b429403
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Connect to and Disconnect from a Host File System
The first step in accessing a host file system is to connect to the file system. You must use `HostFileConnection` to access the host file system. After you have connected, you can retrieve, modify, and update the information that you want.  
  
## Procedure  
  
#### To connect and disconnect to a Host File System  
  
1.  Create a `HostFileConnection` object, using the connection string that describes the Host system.  
  
2.  Open a connection with a call to `HostFileConnection.Open`.  
  
3.  Interact with the host file system as necessary.  
  
4.  When you are finished, release the `HostFileConnection` object with a call to `HostfileConnection.Close` and `HostFileConnection.Dispose`.  
  
     Connections are not implicitly released when a `HostFileConnection` falls out of scope. Therefore, you need to release the object when you are finished using it.  
  
## Example  
 The following very simple code example shows how to use `HostFileConnection` to open and close a connection.  
  
```  
try  
   {  
      HostFileConnection cn = new HostFileConnection();  
      cn.ConnectionString = cnstring;  
      cn.Open();  
      // Perform tasks here.  
      cn.Close();  
      cn.Dispose();  
   }  
```  
  
## See Also  
 [Working with the Managed Data Provider For Host Files](../core/working-with-the-managed-data-provider-for-host-files1.md)   
 [BizTalk Adapter for Host Files Configuration](../core/biztalk-adapter-for-host-files-configuration2.md)