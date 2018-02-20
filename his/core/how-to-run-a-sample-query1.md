---
title: "Run a Sample Query | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60a5bc43-baa3-4a56-ac02-0061cf97169c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Run a Sample Query
One of the final checks you can perform on a created connection string is a simple query that fetches a list of available files and data sources in the target database. Once you create the connection string, you can run this query using DataAccessControl.`Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.SampleQuery%2A?displayProperty=fullName`.  
  
## Run a sample query  
  
1.  Create or retrieve the connection string on which you run the sample query.  
  
     For more information on creating and retrieving connection strings, see [Creating a Connection String](../core/creating-a-connection-string1.md) and [How to Retrieve Data](../core/how-to-retrieve-data2.md).  
  
2.  Run the sample query with a call to `Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.SampleQuery%2A`.  
  
     If successful, `Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.SampleQuery%2A` returns a data table with the relevant values. Otherwise, the method returns null.  
  
## See Also  
 [Performing Administrative Tasks](../core/performing-administrative-tasks1.md)