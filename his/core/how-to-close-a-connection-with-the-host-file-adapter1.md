---
title: "How to Close a Connection with the Host File Adapter1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64f660c7-a6cf-45f1-8cdc-382e4cec9d9c
caps.latest.revision: 3
---
# How to Close a Connection with the Host File Adapter
If you create a HostFileDataAdapter object with a connection string, the object will automatically create a connection object. Once you are finished using a host file adapter, you need to dispose of the implicit connection you made. You can use the Dispose and Close commands to do so.  
  
### To close the connection created implicitly through a HostFileDataAdapter object  
  
1.  Once you are finished with the connection, call HostFileDataAdapter.Dispose() to dispose of the connection.  
  
2.  Alternately, you may also call HostFileDataAdapter.SelectCommand.Connection.Close() to close the connection as well.  
  
## Example  
 The following code sample shows how to create a connection through a HostFileDataAdapter object, and how to properly dispose of the connection.  
  
```  
try  
{  
    HostFileDataAdapter hfda = new HostFileDataAdapter(SELECT,"valid connection string");  
    DataSet ds = new DataSet();  
    hfda.Fill(ds);  
    string xml = ds.GetXml();  
    Console.WriteLine(xml);  
    hfda.Dispose();  
}  
catch (Exception e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
## See Also  
 [Working with the Host File Adapter and Dataset](../core/working-with-the-host-file-adapter-and-dataset1.md)