---
title: "Control Flow in BizTalk Adapter for JD Edwards OneWorld | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connection pooling"
  - "control flows"
  - "apartment threading"
  - "apartment threading, business functions"
ms.assetid: 1ec865d0-2257-453b-9230-1f3787ebac38
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Control Flow in BizTalk Adapter for JD Edwards OneWorld
This topic discusses the design time and run-time control flows in Microsoft BizTalk Adapter for JD Edwards OneWorld.  
  
## Design-Time Flow  
 When the adapter opens (using the credentials and system information from the Transport Properties dialog box), one or more instances of the JD Edwards OneWorld application business function are created and pooled. When you browse the namespace in the Adapter Wizard, a list of business functions appear. Clicking a business function displays its logical methods along with the methods signatures.  
  
## Run-Time Flow  
 Instances of the JD Edwards OneWorld business function are created and pooled for each thread. When a method call is submitted to a business service, the metadata for the method is read using the JD Edwards OneWorld application business function; however, if the metadata for the method has already been cached, the business function uses the cached information and then makes a call to the appropriate method. At run time, a JD Edwards OneWorld interface layer is dynamically constructed. It is through the interface layer that BizTalk Adapter for JD Edwards OneWorld supports invocation and data conversions.  
  
 BizTalk Adapter for JD Edwards OneWorld maps interface descriptions of the method signatures of the JD Edwards OneWorld application, allowing BizTalk Server to interact with these interface descriptions.  
  
 The adapter enables applications in the enterprise to interact with the JD Edwards OneWorld application by extending functionality from the application in the form of one or more of the following:  
  
- Native data formats  
  
- Procedures  
  
- Methods  
  
- Messages  
  
- Properties  
  
- Application interfaces  
  
  At run time, BizTalk Adapter for JD Edwards OneWorld builds a description of application interfaces for client applications that interact with JD Edwards OneWorld. The adapter can create, delete, and invoke business objects as needed, to perform computations in the application and directly invoke methods. All calls into JD Edwards OneWorld are synchronous calls. The adapter receives the XML messages from BizTalk Server, encloses the messages in a SOAP envelope, and transforms the data for the call from SOAP messages into Java types.  
  
  The reply is sent back following a similar process:  
  
1.  The Java types are transformed into SOAP messages.  
  
2.  The SOAP messages are converted into XML messages.  
  
3.  The XML messages are submitted to BizTalk Server for further processing.  
  
### Apartment Threading of Business Functions  
 A JD Edwards OneWorld business function, and any instance, can only be used on the thread where it is created or obtained. This is known as *apartment threading*. The connection pooling framework of BizTalk Adapter for JD Edwards OneWorld manages a pool of available connections.  
  
### Connection Pooling  
 Connection pooling improves the performance of calls by keeping connections to the server systems open and reusing them instead of closing them after each call. BizTalk Adapter for JD Edwards OneWorld enables you to pool connections within particular logon IDs, but still maintains critical control of the total number of connections across all pools.  
  
 Any new business function instance uses the thread on which it is created, and the instance is destroyed after each operation. All JD Edwards OneWorld calls to business functions are stateless; however, during the operation, the adapter ensures that the business function is used on the correct thread.  
  
## See Also  
 [Developing Applications](../core/developing-applications3.md)   
 [Planning and Architecture](../core/planning-and-architecture17.md)