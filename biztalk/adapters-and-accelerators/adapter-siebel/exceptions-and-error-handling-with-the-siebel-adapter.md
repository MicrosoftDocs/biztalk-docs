---
description: "Learn more about: Exceptions and Error Handling with the Siebel adapter"
title: "Exceptions and Error Handling with the Siebel adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Exceptions and Error Handling with the Siebel adapter
## Exception list
The exceptions thrown by the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]. These can contain:  
  
- An inner exception, which is a system exception that the .NET Framework throws  
  
- An LOB exception that the LOB client library throws.  
  
  For more information about the inner exception, refer to the respective .NET Framework or Siebel documentation. The exception also contains a detailed error message that helps in resolving the problem. Note that the list of exceptions mentioned here is not comprehensive.  
  
|Exception|Possible Cause/Error Description|  
|---------------|---------------------------------------|  
|ConnectionException|The adapter throws this exception if it is unable to establish a connection or close an existing connection to a Siebel system.|  
|CredentialsException|The adapter throws this exception if the adapter client does not specify a user name or password to connect to a Siebel system.|  
|MetadataException|The adapter throws this exception if it fails to retrieve metadata for Siebel artifacts.|  
|XmlReaderParsingException|The adapter throws this exception if the input information provided by the adapter clients to invoke an operation in the Siebel system, is either incomplete or incorrect.|  
|XmlReaderGenerationException|The adapter throws this exception if it is unable to generate output for an operation executed in a Siebel system.|  
|TargetSystemException|The adapter throws this exception if the Siebel COM API, which the adapter uses to interface with the Siebel system, throws an exception. The inner exception contains the exception thrown by the Siebel COM API.|  
  
## See Also  
 [Understand BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)   
[Troubleshoot the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)
