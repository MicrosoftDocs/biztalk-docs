---
description: "Learn more about: How to Obtain a Single Value from a Host File System"
title: "How to Obtain a Single Value from a Host File System1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Obtain a Single Value from a Host File System
You might need to return database information that is just a single value rather than in the form of a table or data stream. For example, you might want to return the result of an aggregate function such as COUNT(*), SUM(Price), or AVG(Quantity).  
  
### To obtain a single value from the Host File System  
  
1.  Make a call to `HostFileCommand.ExecuteScalar`.  
  
     `ExecuteScalar` returns a scalar value: the value of the first column of the first row of the result set.  
  
## See Also  
 [Working with the Managed Data Provider For Host Files](../core/working-with-the-managed-data-provider-for-host-files1.md)   
 [BizTalk Adapter for Host Files Configuration](./biztalk-adapter-for-host-files-configuration1.md)
