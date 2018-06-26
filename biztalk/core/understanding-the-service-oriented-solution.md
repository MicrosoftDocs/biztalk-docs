---
title: "Understanding the Service Oriented Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service solution tutorial, background information"
  - "service solutions, about service solutions"
  - "service solution tutorial, about service solution tutorial"
  - "Service Oriented Architecture (SOA)"
ms.assetid: 56a2ad90-74bb-489a-ab1d-900f3bea3d64
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Understanding the Service Oriented Solution
The service oriented solution presents a credit balance reporting application designed as a service. The application, in turn, uses three backend applications, exposed as services themselves, to get the information needed for the credit balance.  
  
 A Service Oriented Architecture (SOA) is an approach that partially overlaps building distributed systems. A service-oriented approach has several characteristics:  
  
- Loosely coupled. The application's business logic is separate from the logic of handling the service.  
  
- Discoverable. There should be a mechanism for applications to find the service.  
  
- Contractual. The interface to the service implements the contract between users and the service.  
  
  Although the literature often treats service oriented approaches as synonymous with web services, they are not necessarily synonyms. Web services present an attractive way to implement service oriented solutions, but you can use other technologies, such as .NET remoting, to create services.  
  
  For more information about service oriented architectures, see "Service Interface" at [http://go.microsoft.com/fwlink/?LinkId=46185](http://go.microsoft.com/fwlink/?LinkId=46185) and "Service-Oriented Integration" at [http://go.microsoft.com/fwlink/?LinkId=46186](http://go.microsoft.com/fwlink/?LinkId=46186).  
  
## Reader Guidance  
 The documentation for this solution assumes that you are familiar with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. It also assumes that you understand basic concepts about enterprise application integration and web services.  
  
 In addition, to read and follow the developer documentation, you should be familiar with how to build applications by using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and with performing the following tasks: creating projects, setting references, and debugging and testing BizTalk solutions.  
  
## Credit Card Reporting at Woodgrove Bank  
 The service oriented architecture solution is a credit card balance reporting service for Woodgrove Bank. Although the bank is fictional, the scenario is not—the scenario is based on an actual, deployed, customer application.  
  
 In the scenario, requests for credit card balances come from two sources:  
  
- An Interactive Voice Response (IVR) application.  
  
- An interactive client such as a web page or custom client application.  
  
  The solution receives requests from the IVR application through MQSeries. It handles requests from the interactive client through a web service using HTTP and SOAP.  
  
  New service oriented architecture applications often need to work with legacy applications that use older technologies, as well as function with modern applications such as web sites that consume web services. The scenario models this real world requirement—the IVR application represents a legacy application, while the customer service client application, is the modern one.  
  
  The Woodgrove Bank application uses data from three backend, legacy systems to respond to requests:  
  
- An application that provides the overall credit limit. This is a SAP system on a mainframe computer.  
  
- A pending transactions system that reports the total amount for transactions pending against the account. This system is a mainframe or AS/400 system. The solution uses a web service and Microsoft Host Integration Server (HIS) to communicate with the mainframe or AS/400 system.  
  
- A payment tracking system that gives the last payment made to the system. The payment tracking system can be reached using MQSeries.  
  
  After gathering and compiling the information from the legacy systems, the solution sends the response back to the originating application and, thus, to the customer.  
  
## Business Requirements  
 Because the credit reporting application responds in real time to customer requests, it must have low latency in order to handle requests quickly. In addition, it must also be able to handle high numbers of simultaneous requests. The solution uses sensitive information and a public interface so that security is significant concern. Finally, the service needs to be reliable.  
  
 For information about how the solution meets these requirements, see [Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md).  
  
## Performance Characteristics  
 To meet the business requirements, the scenario has the following performance characteristics:  
  
-   Sustained throughput of 40 incoming requests per second.  
  
-   Peak throughput of 100 incoming requests per second.  
  
-   90 percent of the requests to be serviced (in and out of BizTalk Server) in under 1000 milliseconds.  
  
-   95 percent of the requests to be serviced (in and out of BizTalk Server) in under 2000 milliseconds.  
  
-   100 percent of the requests to be serviced (in and out of BizTalk Server) in under 5000 milliseconds.  
  
> [!NOTE]
>  These times do not include the latency times of the back end systems.  
  
## Three Versions of the Solution  
 There are three versions of the solution:  
  
- The stub version replaces all of the backend systems with software stubs. The stubs simulate the backend systems. This version provides a quick way to deploy and run the solution on a single computer.  
  
- The adapter version uses BizTalk adapters to connect to the backend systems. This version is how one might first think to implement the solution. However, sending messages to the backend systems using the adapters introduces significant latency in getting back responses. While adapters by themselves could offer very low latency, the distributed architecture of BizTalk Server requires adapters to communicate with the orchestration host instances using the message box. This introduces round trips to the database and affects latency times.  
  
- The inline version replaces the adapters with inline code that communicates directly with the backend systems. The inline version of the solution has the lowest latency and the highest throughput.  
  
  The deployment guide provides directions for building and deploying all three versions of the solution, as well as providing a way, in each version, to simulate the connection through HIS to the pending transactions system. For information about building and deploying the solution, see [Deploying the Service Oriented Solution](../core/deploying-the-service-oriented-solution.md).  
  
## See Also  
 [Service Oriented Solution](../core/service-oriented-solution.md)