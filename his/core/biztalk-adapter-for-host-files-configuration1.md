---
title: "BizTalk Adapter for Host Files Configuration1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e346515-129b-4170-80ba-9b9628dd5359
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Adapter for Host Files Configuration
The BizTalk Adapter for Host Files is a send and receive adapter that enables BizTalk orchestrations to interact with host systems. Specifically, the adapter enables send and receive operations over TCP/IP and APPC connections to host files that run on mainframe and AS/400 platforms. Based on Host Integration Server technology, the adapter uses Data Access Library metadata assemblies to configure connections, and the Microsoft .NET Framework data provider for host files to issue SQL commands and stored procedures.  
  
 The adapter serves two main functions:  
  
-   For **Send** operations (both One Way and Solicit Response), the adapter sends SQL commands and system commands to a host file instance, with the option of soliciting a response.  
  
-   For **Receive** operations (One Way only) the adapter creates an SQL command that polls host file objects and creates per-row messages, which are then submitted to the BizTalk message system.  
  
 In addition, the BizTalk Adapter for Host Files uses the standard BizTalk Adapter tracing tool as a troubleshooting mechanism.  
  
> [!NOTE]
>  The BizTalk Adapter for Host Files is a non-transactional adapter. This means that once an action is performed, it cannot be undone or rolled back.  
  
## In This Section  
 [How to Create a Metadata Assembly for the Host File Adapter](../core/how-to-create-a-metadata-assembly-for-the-host-file-adapter1.md)  
  
 [How to Create a Send Port for the Host File Adapter](../core/how-to-create-a-send-port-for-the-host-file-adapter1.md)  
  
 [How to Create a Receive Port and a Receive Location for the Host File Adapter](../core/how-to-create-a-receive-port-and-a-receive-location-for-the-host-file-adapter2.md)  
  
 [How to Create a Schema for the Host File Adapter](../core/how-to-create-a-schema-for-the-host-file-adapter2.md)  
  
 [How to Create a BizTalk Application for the Host File Adapter](../core/how-to-create-a-biztalk-application-for-the-host-file-adapter2.md)  
  
## See Also  
 [Data Access Library &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/da533736-8ecc-4466-a13d-b635696d94c8)   
 [Managed Data Provider for Host Files](../core/managed-data-provider-for-host-files1.md)