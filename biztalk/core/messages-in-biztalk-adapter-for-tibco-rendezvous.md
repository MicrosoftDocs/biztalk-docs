---
title: "Messages in TIBCO Rendezvous adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12699550-22e7-4a11-a024-2302570970af
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Messages in BizTalk Adapter for TIBCO Rendezvous
BizTalk Adapter for TIBCO Rendezvous provides bi-directional connectivity between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and TIBCO Rendezvous. This adapter uses both the TIBCO Rendezvous API and the BizTalk Adapter Framework API to provide tight integration.  
  
## About TIBCO Rendezvous  
 TIBCO Rendezvous is a programs that provides a message bus for enterprise application integration (EAI). TIBCO provides messaging APIs in C, C++, Java, Visual Basic and for the Microsoft .NET Framework to receive data feeds on Microsoft Office Excel worksheets and other applications of choice. For more information, see [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md).  
  
## Message Passing  
 The basic concept of message passing is fairly simple:  
  
- A message has a single subject composed of elements separated by periods. A message is sent to a single Rendezvous daemon, although it might eventually be broadcast onto other daemons.  
  
- A listener announces its subjects of interest to a daemon (with a basic wildcard facility). Messages that have matching subjects are delivered to it if the two daemons are connected to each other, or are indeed the same daemon.  
  
  Significant "Enterprise" functionality is layered onto this if desired--with Fault Tolerance/Reliable or Certified options possible--all implemented through the underlying basic messages.  
  
  The messages themselves can be viewed as typed name-value fields or number-value fields (the two identification mechanisms in a message can mix and match with certain restrictions). A message itself can contain sub-messages, which can contain sub-messages.  
  
  Subject names consist of one or more elements separated by dot characters (periods). The elements implement a subject name hierarchy that reflects the structure of information in an application system. The following strings are examples of valid subject names:  
  
- RUN.HOME  
  
- RUN.for.Elected_Office  
  
  BizTalk Adapter for TIBCO Rendezvous uses the TIBCO Rendezvous SDK to publish messages to TIBCO Rendezvous subjects and to register for TIBCO Rendezvous events. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related classes are hosted in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer. A separate process (run-time agent) is started and acts as the Rendezvous program, and .NET Framework remoting is used to exchange messages between the two.  
  
- Info-Level, Warning-Level, and Error-level messages are sent to the Windows event log.  
  
- All levels, including Debug-level messages, are sent to the Windows Tracing Log.  
  
## Transmitter  
 BizTalk Adapter for TIBCO Rendezvous launches one run-time agent per send port. The TIBCO Rendezvous .NET Framework API only allows setting character encoding at a global scope. Therefore, one of the port configuration options is a code page number. By starting a different process for each code page, the adapter can provide better support for globalization.  
  
## Receiver  
 BizTalk Adapter for TIBCO Rendezvous launches one run-time agent per receive location.  
  
## Transactions  
 The TIBCO Rendezvous product is not transactional. A separate product, TIBCO Rendezvous TX, is required. BizTalk Adapter for TIBCO Rendezvous does not support transactions in this release.  
  
## Security  
 TIBCO Rendezvous only supports authentication between TIBCO Rendezvous programs and daemons. It does not perform authorization or encryption. A separate product, TIBCO Rendezvous DataSecurity, is required.  
  
## See Also  
 [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md)   
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)