---
title: "Common Issues with the BAM Interceptors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a32145e2-1367-4576-9103-86c9182c11a8
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Common Issues with the BAM Interceptors
This topic discusses the following common problems that can arise when using BAM interceptors:  
  
-   SQL Exception relating to a distributed transaction  
  
## You Receive a SQL Exception Concerning a Completed Distributed Transaction or a Transaction Descriptor  
 You may see one of the following exceptions when running the BAM Windows Communication Framework (WCF) interceptor:  
  
- Distributed transaction completed. Either enlist this session in a new transaction or the NULL transaction.  
  
- New request is not allowed to start because it should come with a valid transaction descriptor.  
  
  Some suggestions for troubleshooting this problem are:  
  
- Enable BAM tracing. This trace will include all relevant messages including the root cause of the error. For more information about BAM tracing, see [How to Enable Tracing in BAM](../core/how-to-enable-tracing-in-bam.md).  
  
- When you see this distributed transaction coordinator (DTC) exception, try to rerun exactly the same scenario without transactions.  
  
- Use SQL Server Profiler and look for errors in the trace that will cause the transaction to be aborted.  
  
## You receive an error similar to "interceptor configuration polling interval '0' must be at least '5' seconds" when using the WCF Interceptor  
 You may encounter this error when you do not explicitly provide an interceptor configuration polling interval value in the application configuration file, or when you provide a value but it is less than 5 seconds, the required minimum.  
  
 To fix the problem, provide a valid value for PollingIntervalSec as shown:  
  
```  
<BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" PollingIntervalSec="1500" />  
```  
  
## See Also  
 [Troubleshooting BAM Interceptors](../core/troubleshooting-bam-interceptors.md)