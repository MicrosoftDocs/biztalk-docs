---
title: "How to Run a Sample Query2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50bbeb40-ca21-4ed9-b28a-14af8c57cf8b
caps.latest.revision: 4
---
# How to Run a Sample Query
One of the final checks you can perform on a created connection string is a simple query that fetches a list of available files and data sources in the target database. Once you create the connection string, you can run this query using DataAccessControl.<xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.SampleQuery%2A?displayProperty=fullName>.  
  
### To run a sample query  
  
1.  Create or retrieve the connection string on which you run the sample query.  
  
     For more information on creating and retrieving connection strings, see [Creating a Connection String](../HIS2010/creating-a-connection-string2.md) and [How to Retrieve Data](../HIS2010/how-to-retrieve-data1.md).  
  
2.  Run the sample query with a call to <xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.SampleQuery%2A>.  
  
     If successful, <xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.SampleQuery%2A> returns a data table with the relevant values. Otherwise, the method returns null.  
  
## See Also  
 [How to Run a Sample Query &#91;bpi&#93; &#91;HIS09_R2&#93;](http://msdn.microsoft.com/en-us/2fca9cac-ad84-409d-9171-6cd0dfb33b0a)   
 [Performing Administrative Tasks](../HIS2010/performing-administrative-tasks2.md)