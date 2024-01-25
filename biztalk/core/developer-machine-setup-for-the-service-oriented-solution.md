---
description: "Learn more about: Developer Machine Setup for the Service Oriented Solution"
title: "Developer Machine Setup for the Service Oriented Solution"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Developer Machine Setup for the Service Oriented Solution
Service Oriented Architecture (SOA) is an approach to building distributed systems. The service oriented solution demonstrates how several back-end systems using different protocols can be aggregated into a single service that clients can consume. This solution integrates services with an approach that guarantees delivery and performance characteristics for the service level agreement that you need to satisfy.  
  
 The service oriented solution is modeled after a service-level agreement scenario in which BizTalk Server and the Line of Business (LOB) application servers connected to it are given three seconds to respond with a service request. One of those three seconds may be taken up by the BizTalk Server.  
  
 There are three versions of the service oriented solution: adapter, inline, and stub. For more information about the differences between three versions of the service-oriented solution, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md). As a developer, you get the scenario running by using the stub version of the scenario. This version does not require any LOB back-end servers in order to run. After this you can use the adapter version of the scenario to learn how various adapters and back-end servers can be integrated and configured to respond using the BizTalk servers as a single service. You can then measure the latency induced by BizTalk Server and its adapters.  
  
 If the latency for the BizTalk server is in excess of its service requirement, you can bypass the LOB adapter persistence points by installing and running the SOA in-line version. This version bypasses the adapters and subsequently their latency contributions due to the MessageBox persistence point. Instead, the inline version talks straight to the back-end servers through Remote Procedure Calls (RPC) mechanisms such as DCOM.  
  
 For more information about the MessageBox persistence point, see [Persistence and the Orchestration Engine](../core/persistence-and-the-orchestration-engine.md).  
  
 This deployment guide describes how to install and test the three versions of the service-oriented solution on a single computer.  
  
 For more information about the service-oriented solution, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).  
  
## In This Section  
  
-   [Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md)  
  
-   [How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)  
  
-   [How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)  
  
-   [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md)
