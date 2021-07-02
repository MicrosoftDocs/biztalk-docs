---
description: "Learn more about: Sample Architecture: HTTP and SOAP Adapters"
title: "Sample Architecture: HTTP and SOAP Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "examples, security"
  - "architecture, examples"
  - "SOAP adapters, security"
  - "Web Publishing"
  - "security, examples"
  - "security, architecture"
  - "SOAP adapters, architecture examples"
  - "examples, architecture"
  - "architecture, security"
  - "HTTP adapters, architecture examples"
  - "reverse proxy rules"
  - "ISA Server implementation"
  - "HTTP adapters, security"
ms.assetid: 935197d0-5108-4970-b237-3c6d5b40c5e9
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sample Architecture: HTTP and SOAP Adapters
This topic describes the sample architecture when you use the HTTP and SOAP adapters to send and receive messages.

 The following figure shows the components of the BizTalk Server sample architecture when you use the HTTP or SOAP adapters.

 **Figure 1 Sample architecture that shows HTTP or SOAP adapters**

 ![Sample architecture for HTTP or SOAP adapter](../core/media/tdi-sec-refarch-http.gif "TDI_Sec_RefArch_HTTP")

 This sample architecture contains the components as discussed in the following sections.

## Perimeter network―Internet
 When you use the SOAP and HTTP adapters, we recommend that you use reverse proxy rules (the TMG Server implementation is called Web Publishing) to relay the message from the Internet-facing firewall (Firewall 1) to the firewall that helps protect the E-Business domain (Firewall 2), and from this firewall to the BizTalk Server that runs the isolated host. For more information about Web Publishing rules, see the Microsoft Web site at [https://go.microsoft.com/fwlink/?LinkID=205340](/previous-versions/tn-archive/cc984490(v=technet.10)) (https://go.microsoft.com/fwlink/?LinkID=205340).

> [!NOTE]
>  When you use reverse proxy, you do not need Web servers in the perimeter network.

## Perimeter network―intranet
 Companies commonly use the HTTP and SOAP protocols for Internet-based communications, and therefore you do not need any servers in the intranet perimeter network to support this scenario. If you have an internal application in the intranet that integrates with BizTalk Server through the HTTP or SOAP protocols, you should follow the recommendations for the Internet perimeter network.

## E-Business domain
 This domain contains all the infrastructure and applications used by your BizTalk Server implementation. The servers in this domain are:

-   **BizTalk Server (processing and tracking hosts).** This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes. This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data.

    > [!NOTE]
    >  As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.

-   **BizTalk Server (isolated hosts for SOAP and HTTP adapters).** This server has an installation of the BizTalk Server runtime, and has only instances of the hosts that contain the HTTP and SOAP adapters. These hosts run in a separate server because these adapters require that you install Internet Information Services (IIS) on the computer where they run.

    > [!NOTE]
    >  As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your HTTP and SOAP adapter hosts. When you do this, you must also configure Network Load Balancing (NLB). For more information about how to configure BizTalk Server for high availability, see [Planning for High Availability](../core/planning-for-high-availability3.md).

-   **Master secret server.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).

-   **SQL Server.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).

-   **Domain controller.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).

-   **Administration tools.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).

## See Also
 [Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md)
 [Sample Scenarios for Threat Model Analysis](../core/sample-scenarios-for-threat-model-analysis.md)