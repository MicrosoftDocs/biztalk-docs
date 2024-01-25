---
description: "Learn more about: TIBCO Enterprise Message Service Requirements and Limitations"
title: "TIBCO Enterprise Message Service Requirements and Limitations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TIBCO Enterprise Message Service Requirements and Limitations

## System Requirements  
Included with TIBCO Enterprise Message Service includes a client SDK (using the TIBCO EMS C# API). BizTalk Adapter for TIBCO EMS uses this API to communicate with TIBCO EMS.  
  
## Add the API to the GAC  
 BizTalk Adapter for TIBCO EMS requires the TIBCO EMS C# API, TIBCO.EMS.dll, to be added to the global assembly cache (GAC). The adapter triggers an exception and logs an appropriate message if this assembly is not installed.  
  
1. Copy the TIBCO EMS C#API to your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.  
  
2. Change directories to the location of the C# API file, TIBCO.EMS.DLL.  
  
    In the default installation, the path to this DLL is c:\tibco\ems\clients\cs\TIBCO.EMS.DLL.  
  
3. In a command prompt, type:  
  
    `C:\bin> gacutil /i TIBCO.EMS.dll`  
  
    The TIBCO.EMS.dll now shows the GAC.  
  
    To view the GAC list, in Control Panel, open **Administrative Tools**, open **Microsoft .NET Framework X.XConfiguration**, and then click **Assembly Cache**.  
  
## Limitations  
 BizTalk Adapter for TIBCO Enterprise Message Service uses TIBCO.EMS.dll to communicate with TIBCO Enterprise Message Service. You should consider the following limitations when you use the TIBCO EMS C# API:  
  
-   Message compression, which enables the TIBCO EMS client to send messages in a compressed form to EMS, is not available with the C# API.  
  
-   Encryption of messages between the adapter and the server is not available with the C# API. The C# API does not allow for SSL encryption using the OpenSSL libraries.  
  
-   The C# API does not support the Administration API for EMS.  
  
-   Messages greater than 50MB in size cannot be sent or received using the BizTalk TIBCO EMS adapter. Beyond this size, the environment experiences System.OutOfMemoryException exceptions.  
  
## See Also  
 [Planning and Architecture](../core/planning-and-architecture16.md)
