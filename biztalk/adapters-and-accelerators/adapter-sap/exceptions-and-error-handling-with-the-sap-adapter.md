---
title: "Exceptions and Error Handling with the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exceptions and error handling"
  - "error handling, troubleshooting"
  - "troubleshooting, exceptions and error handling"
ms.assetid: 598a25c5-6905-4c0c-835b-159d827b2269
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Exceptions and Error Handling with the SAP adapter
Lists the exceptions that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] throws. These can contain:  

- An inner exception, which is a system exception that the .NET Framework throws  

- An LOB exception that the LOB client library throws.  

  For more information about the inner exception, see the .NET Framework or SAP documentation. Exceptions also contain a detailed error message that may help resolve the problem.  

## Exception descriptions  

|Exception|Possible Cause/Description|  
|---------------|---------------------------------|  
|ObjectDisposedException|The adapter throws this exception when the adapter client is trying to access the response XMLReader after it has been disposed.|  
|XmlReaderGenerationException|The adapter throws this exception when it is unable to generate an XmlReader from the output message. This could also be due to some problems with the data received from the SAP system. Look for the inner exception and the error message for more information.|  
|InvalidUriException|This exception is thrown when the connection URI does not have the required components for the connection string.|  
|ConnectionException|This exception is thrown when there is a problem connecting to the SAP system or if an underlying connection becomes invalid, either due to an error on the SAP system or due to a network problem.|  
|TimeoutException|This exception is thrown when the timeout specified for an operation is lapsed. The inner exception contains the specifics of why the specified timeout was not sufficient.|  
|XmlReaderParsingException|The adapter throws this exception if it does not support the specified type, or if an incorrect value is specified for the type. Also, the input XML could be incorrect. An incorrect value includes cases where the maximum amount of text or maximum digits is exceeded. The input XML might be incorrect if the operation name or namespace is incorrect.|  
|RFCException (derived from AdapterException)|The adapter throws this exception if there is an error received from the SAP system. The inner exception is the actual exception received from the SAP system.|  
|UnsupportedOperationException|The adapter throws this exception when the adapter client specifies an invalid action.|  
|MetadataException|The adapter throws this exception if there is an error during metadata retrieval, browse, or search.|  

## See Also  
[Troubleshoot the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)