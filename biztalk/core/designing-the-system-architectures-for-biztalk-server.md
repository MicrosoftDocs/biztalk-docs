---
description: "Learn more about: Designing the System Architectures for BizTalk Server"
title: "Designing the System Architectures for BizTalk Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Designing the System Architectures for BizTalk Server
The requirements of your Microsoft® BizTalk® Server deployment for security, performance, availability, and operation are highly dependent on your business needs, requirements, partners, company size, and so on. While it is difficult to consider any single configuration of BizTalk Server components as typical and provide prescriptive guidance for it, this section provides guidance and recommendations on how to configure the different BizTalk Server features in a distributed, secure configuration for the production environment of a large enterprise.  
  
 The architectures presented in this section aim to provide you with reference information about deploying BizTalk Server in a highly distributed environment where you take into consideration defense in depth. Every application for BizTalk Server is likely to have its own unique set of security requirements based on the problem domain, the protocols used, and the particular environment the solution operates in. Performance, availability, and cost considerations further influence these requirements. You should use these architectures and the recommendations within this document as the building blocks to create your own BizTalk Server deployment tailored to the needs, threats and assets of your company.  
  
 This section contains information about how you can design the system architecture for BizTalk Server to secure the different features in BizTalk Server, and consequently, secure the data that the servers process and store, and how to place the servers in a distributed environment that minimize the potential for critical data and servers being compromised in the event of an attack or disaster. This section does not provide recommendations for configuring development, or test environments, or details for deploying an assembly into a production environment. For more information about deploying assemblies, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).  
  
## In This Section  
  
-   [Designing a Secure Architecture](../core/designing-a-secure-architecture.md)  
  
-   [Designing a Distributed Architecture](../core/designing-a-distributed-architecture.md)  
  
-   [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md)
