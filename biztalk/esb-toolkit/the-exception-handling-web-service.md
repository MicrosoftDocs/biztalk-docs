---
title: "The Exception Handling Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfe6ebdf-9b92-40c7-93fb-afd6c5f68aaa
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Exception Handling Web Service
The Exception Handling Web service accepts a fault message and publishes it to the ESB Exception Portal. A client application can create exception messages and submit them to the ESB, where any handler configured for that exception type, or a generic handler, can process the exception. The major benefit of this service is that it allows entities outside an ESB application to participate in the ESB exception handling mechanism.  
  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains two versions of this service: an ASP.NET (ASMX) version and a Windows Communication Foundation (WCF) version. The service names are **ESB.ExceptionHandlingServices** and **ESB.ExceptionHandlingServices.WCF**, respectively, and the services expose a single method:  
  
- **SubmitFault**. This method takes an instance of the **FaultMessage** class and has no return value.  
  
  For information about the way the exception handling mechanism works, see [Using ESB Exception Management](../esb-toolkit/using-esb-exception-management.md).  
  
> [!NOTE]
>  By default, the Exception Handling Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients. You should configure the service so that it requires SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and the server that hosts the **ESBExceptions** database using network-level IPSec and appropriate file-level access control list (ACL) permissions.