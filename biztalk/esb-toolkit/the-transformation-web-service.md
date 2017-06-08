---
title: "The Transformation Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 788bf4a9-a63b-4fd3-93a2-6e34a1464049
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Transformation Web Service
The Transformation Web service enables external applications to submit a document to an ESB application and have it transformed using a deployed Microsoft BizTalk map. Unlike the transformation agent, this service does not route messages through the BizTalk Message Box database.  
  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains two versions of this service: an ASP.NET (ASMX) version and a Windows Communication Foundation (WCF) version. The service names are **ESB.TransformServices** and **ESB.TransformServices.WCF**, respectively, and the services expose a single method:  
  
-   **Transform.** This method takes as parameters a **String** that contains the message to transform and a **String** that contains the fully qualified name of a map deployed in BizTalk. The method returns a **String** that contains the transformed document. The use of string parameters reduces the risk of interoperability issues in a heterogeneous environment; however, keep in mind that this is a Web service, so you should avoid using it to transform large documents (the Transformation Service in BizTalk is better suited for large documents).  
  
> [!NOTE]
>  By default, the Transformation Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients. You should configure the service so that it requires SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and your BizTalk Server using network-level IPSec and appropriate file-level access control list (ACL) permissions.