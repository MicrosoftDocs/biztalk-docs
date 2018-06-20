---
title: "Exceptions and error handling with the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exception, LOB"
  - "exception, inner"
  - "exceptions, error handling"
  - "error handling, exceptions"
ms.assetid: df9a1244-63cd-438e-8a06-99383fbeba2c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Exceptions and error handling with the Oracle Database adapter
This section lists the exceptions that the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] throws. These can contain:  
  
- An inner exception, which is a system exception that the .NET Framework throws.  
  
- An LOB exception that the LOB client library throws.  
  
  For more information about the inner exception, see the respective .NET Framework or Oracle documentation. Exceptions also contain a detailed error message that helps in resolving the problem.  
  
|Exception|Possible Cause/Description|  
|---------------|---------------------------------|  
|XmlReaderParsingException|The adapter throws this exception if it does not support the specified type, or if an incorrect value is specified for the type. Also, the input XML might be incorrect. An incorrect value includes cases where the maximum amount of text or maximum digits is exceeded. The input XML might be incorrect if the operation name or namespace is incorrect.|  
|UnsupportedOperationException|The adapter throws this exception when the adapter client specifies an invalid action.|  
|ArgumentException|The adapter throws this exception if an incorrect value is specified for an argument.|  
|NotImplementedException|The adapter throws this exception if some method in the XMLReader reader is not implemented.|  
|ArgumentNullException|The adapter throws this exception if a required argument is not specified.|  
|ArgumentOutOfRangeException|The adapter throws this exception if it tries to access a non-existent entity or out-of-range entity.|  
|XmlReaderGenerationException|The adapter throws this exception when it is unable to generate an XmlReader from the output message.|  
|MetadataException|The adapter throws this exception if there is an error during metadata retrieval, browse, or search.|  
|CredentialsException|The adapter throws this exception if there is a problem retrieving or using security tokens or if the required credentials are not specified.|  
|InvalidUriException|The adapter throws this exception if the connection URI does not have the required components for the connection string.|  
|ConnectionException|The adapter throws this exception if there is a problem connecting to the Oracle database using ODP.NET. The inner exception contains the Oracle exception.|  
|TimeoutException|The adapter throws this exception if the timeout specified for an operation is lapsed. The inner exception contains the specifics of why the specified timeout was not sufficient.|  
|ListenerException|The adapter throws this exception if there is a problem in receiving a message from the target system. This message denotes a problem related to the Oracle listener. The inner exception has the specifics of the issue.|  
|TargetSystemException|The adapter throws this exception if Oracle returns an error or invalid response. The inner exception contains the Oracle runtime exception.|  
|InvalidOperationException|The adapter throws this exception if adapter tries to perform an invalid operation on the target system. The inner exception contains the specifics of the invalid operation being performed.|  
|OverflowException|The adapter throws this exception if while performing operation containing Oracle numeric data types inside DataSets or weakly-typed REF CURSORS, a large value is specified for these Oracle numeric data types that cannot fit into the respective .NET type.|  
  
## See Also  
[Troubleshoot the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)