---
title: "SOA Governance Integration with the ESB Toolkit in BizTalk Server | Microsoft Docs"
description: List of challenges with SOA-based system and third party integration with ESB Toolkit in BizTalk Server
caps.latest.revision: 3
author: "MandiOhlinger"
manager: "anneta"

ms.custom: ""
ms.date: "08/10/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ccb5ac2d-cd90-414d-a6c7-045a8fe9450b
ms.author: "mandia"
---

# SOA Governance Integration
Enterprise-level applications must support robust and reliable management features to be able to comply with business requirements, government legislation, service level agreements (SLAs), and customer and trading partner expectations. Run-time governance focuses specifically on the challenges of, and requirements for, successfully running service-oriented architecture (SOA)–based systems that meet these requirements. The quality of service delivered by a business system is the predominant factor that defines its success or failure.  

## SOA challenges  
 Businesses deploying SOA-based systems into production face a number of challenges, including the following:  

-   Minimizing the cost of maintenance and upgrades, and allowing incremental updates  

-   Allowing rapid change through business process management and composition tools  

-   End-to-end security; this includes trust and protection of the privacy of message senders, receivers, and content  

-   Identifying, managing, and repairing exceptions as they occur  

-   Decoupling of services and consumers  

-   Measuring and proving the business value of SOA applications to offset cost concerns  

-   Control (governance) of the proliferation of duplicate or otherwise unnecessary services  

-   Facilitating the identification of the appropriate services required by potential users to reduce initial development cost  

-   Managing the life cycle of services to minimize the cost and risk of ongoing maintenance and change  

-   Simplifying the actual usage of appropriate services (decoupling location, transport, policies, standards, and messaging styles)  

-   Reporting facilities used to identify who is using which service, where, and why  

## Next steps
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports integration with two third-party run-time governance systems:  

- **Sentinet SOA Resolver and BizTalk Server Extensions**. For more information on how Sentinet extends [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] capabilities, see [Extending BizTalk ESB Toolkit Capabilities with Sentinet](../technical-guides/extending-biztalk-esb-toolkit-capabilities-with-sentinet.md).

- [SOA BizTalk Management Point](../esb-toolkit/soa-biztalk-management-point.md) from SOA Software, Inc.  

- [AmberPoint BizTalk Nano Agent](../esb-toolkit/amberpoint-biztalk-nano-agent.md) from AmberPoint, Inc.
