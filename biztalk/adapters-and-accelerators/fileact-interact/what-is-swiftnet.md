---
title: "What Is SWIFTNet? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b074385-352c-40f4-b73e-1891c627aa4e
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is SWIFTNet?
As a general purpose, industry-standard solution for the financial industry, SWIFTNet provides an application-independent, single window interface to all the connected applications of all the institutions participating in the global financial community. Actual access is controlled by the business policy decisions of each Service Administrator, not by the technical limitations of the infrastructure.  
  
 SWIFTNet provides a basis for assuring business continuity and disaster recovery for the infrastructure of mission-critical financial applications that cross institutional boundaries. SWIFTNet is designed to satisfy institutional community requirements for interoperability of mission-critical financial software solutions.  
  
 To interconnected business applications, SWIFTNet provides the following:  
  
-   Assurance of infrastructure reliability  
  
-   Availability  
  
-   Role-based and non-role-based access control  
  
-   Correspondent and message authentication  
  
-   Message integrity  
  
-   Confidentiality  
  
-   Non-repudiation support  
  
-   Message validation  
  
-   Store and-forward  

SWIFTNet uses **SWIFTNet Link** (SNL) as the application programming interface to the SWIFTNet services, and uses the **SWIFTAlliance Gateway** for connectivity and usability. Read more about these resources in this topic.

## SWIFTNet Link overview

Business software applications use the SWIFTNet Link (SNL) application programming interface (API) to access and use SWIFTNet services. The SNL is the mandatory network interface to SWIFTNet. SWIFTNet requires SNL for all external interfaces. The SNL also includes background processes that support messaging, security, and service management functions. The SNL is incorporated into SWIFTAlliance WebStation and SWIFTAlliance Gateway (SAG).  
  
 SNL establishes a loosely coupled client/server relationship between business application components. Instead of directly invoking methods or functions, the interaction is message-oriented: structured messages are passed between client and server. A business application designed for SWIFTNet services generally consists of a set of clients and servers. The same client or the same server process can be started multiple times. Note that you cannot predict to which process instance of the same application an incoming message request will be delivered. Multiple threads within a client process can invoke the SwCall API function. A server process can have multiple threads as well; however, only one thread can invoke SwCallback. Client and server processes cannot be combined in the same process.  
  
 SNL provides a set of transport-level features designed for high availability and high throughput environments. These features include:  
  
- Load balancing  
  
- Location transparency and routing, shielding application components from the underlying transport technology  
  
- Transport-level authentication and confidentiality, packaged within SNL and provided transparently to the application  
  
- Security functions by which business application software may establish end-to-end security (user application to user application), when required.  
  
  In terms of programming at the source code level using C++ or Java, there are only two functions: SwCall and SwCallback. SwCall is used by client applications to access server applications through SWIFTNet. SwCallback is used by server applications to respond to clients through SWIFTNet.  
  
  The SwCall and SwCallback functions access the functionality of SWIFTNet by passing structured XML messages to and from SWIFTNet. At run-time, SNL includes both software libraries — the code of which executes within the same address space as business application client or server processes — and independent processes (daemons or services), which run in their own address spaces. The software libraries are accessible through the SNL APIs.  

## SWIFTAlliance Gateway overview
  
The SWIFTAlliance Gateway (SAG) is an interface product for SWIFTNet. It incorporates all the functionality of the SWIFTNet Link. Additionally, it provides several different connectivity and usability features for SWIFTNet users, providing solutions to a variety of system integration problems.  
  
 The SAG supports several different modes of operation. One of these, the strict SWIFTNet Link Mode, is particularly relevant to the FileAct and InterAct adapters for SWIFT. In strict SWIFTNet Link Mode, the SAG presents a messaging interface that is functionally equivalent to the SWIFTNet Link interface as it is described throughout these topics.  
  
 The SAG serves as a message concentrator. It receives messages from various other applications and passes them through SWIFTNet. It receives these messages through host adapters, including a WebSphere MQ host adapter, which enables business applications running on a variety of different types of computing platforms to pass messages through SWIFTNet.  
 
 ## Next reading
 
 [What Is the FileAct Adapter?](../../adapters-and-accelerators/fileact-interact/what-is-the-fileact-adapter.md)  
 [What Is the InterAct Adapter?](../../adapters-and-accelerators/fileact-interact/what-is-the-interact-adapter.md)  
 [BizTalk FileAct and InterAct Adapters End-to-End Tutorial](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md)
 
 ## See also
 [Understanding FileAct and InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md)