---
title: "How to Execute Commands in the Host File System2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c09dd5f-8749-4e17-8e03-f9d3ced57ca3
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Execute Commands in the Host File System
After establishing a connection to a data source, you can execute commands and return results from the data source using `HostFileCommand`.  
  
> [!IMPORTANT]
>  The Managed Provider for Host Files does not support any type of transaction. Therefore, you should try to avoid using INSERT, UPDATE, or DELETE commands on mission-critical data.  
  
## Procedure  
  
#### To execute a command on the host file system  
  
1.  Establish a connection using `HostFileConnection`.  
  
     For more information, see [How to Connect to and Disconnect from a Host File System](../core/how-to-connect-to-and-disconnect-from-a-host-file-system.md).  
  
2.  Once connected, create a `HostFileCommand` object by using `HostfileConnection.CreateCommand`.  
  
3.  Use the `HostFileCommand` object to execute commands on the Host File system.  
  
     `HostFileCommand` exposes several Execute methods that you can use:  
  
    -   When returning results as a stream of data, use `ExecuteDbDataReader` to return a `DataReader` object.  
  
    -   Use `ExecuteScalar` to return a singleton value.  
  
    -   Use `ExecuteNonQuery` to execute commands that do not return rows.  
  
    -   Use `ExecuteRecordSet` to execute commands on a recordset.  
  
> [!NOTE]
>  When modifying an Alternate Index File (AIX), you may receive an "Invalid record length" error when the Index is defined not to accept duplicate keys. This error may occur because the INDEX of the Alternate Index VSAM file is not large enough to hold multiple key values for the same index record .  
  
## See Also  
 [Working with the Managed Data Provider For Host Files](../core/working-with-the-managed-data-provider-for-host-files.md)   
 [BizTalk Adapter for Host Files Configuration](../Topic/BizTalk%20Adapter%20for%20Host%20Files%20Configuration2.md)