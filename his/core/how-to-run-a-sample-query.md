---
title: "How to Run a Sample Query1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60a5bc43-baa3-4a56-ac02-0061cf97169c
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Run a Sample Query
One of the final checks you can perform on a created connection string is a simple query that fetches a list of available files and data sources in the target database. Once you create the connection string, you can run this query using DataAccessControl.<xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.SampleQuery%2A?displayProperty=fullName>.  
  
### To run a sample query  
  
1.  Create or retrieve the connection string on which you run the sample query.  
  
     For more information on creating and retrieving connection strings, see [Creating a Connection String](../core/creating-a-connection-string.md) and [How to Retrieve Data](../core/how-to-retrieve-data.md).  
  
2.  Run the sample query with a call to <xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.SampleQuery%2A>.  
  
     If successful, <xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.SampleQuery%2A> returns a data table with the relevant values. Otherwise, the method returns null.  
  
## See Also  
 [How to Run a Sample Query &#91;bpi&#93; &#91;HIS09_R2&#93;](http://msdn.microsoft.com/en-us/2fca9cac-ad84-409d-9171-6cd0dfb33b0a)   
 [Performing Administrative Tasks](../core/performing-administrative-tasks.md)