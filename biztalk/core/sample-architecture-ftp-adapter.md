---
description: "Learn more about: Sample Architecture: FTP Adapter"
title: "Sample Architecture: FTP Adapter | Microsoft Docs"
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
  - "independent software vendor (ISV)"
  - "security, examples"
  - "security, architecture"
  - "examples, architecture"
  - "architecture, security"
  - "FTP adapters, security"
  - "FTP adapters, architecture examples"
ms.assetid: 13fc1086-6acc-483c-be83-4ff6a60cd2bc
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sample Architecture: FTP Adapter
This topic describes the sample architecture when you use the FTP adapter to send and receive messages.  
  
 The following figure shows the components of the BizTalk Server sample architecture when you use the FTP adapter.  
  
 **Figure 1 Sample architecture that shows FTP adapter**  
  
 ![Sample architecture for FTP adapter](../core/media/tdi-sec-refarch-ftp.gif "TDI_Sec_RefArch_FTP")  
  
 This sample architecture contains the components as discussed in following sections.  
  
## Perimeter network―Internet  
 When you use the FTP adapter, there is an FTP server in the Internet perimeter network.  
  
> [!NOTE]
>  The FTP server can also be located outside your environment—in the partner's network, or hosted by a third-party independent software vendor (ISV).  
  
## Perimeter network―intranet  
 Companies commonly use the FTP protocol for Internet-based communications, and therefore you do not need any servers in the intranet perimeter network to support this scenario.  
  
## E-Business domain  
 The servers in this domain are:  
  
-   **BizTalk Server (processing, FTP adapter, and tracking hosts).** This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes. This is where the BizTalk Server ports, receive locations, pipelines, maps, schemas, and assemblies are located to receive, route, process, and send messages. This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data. Additionally, this host contains instances of the host that runs the FTP send and receive adapters.  
  
    > [!NOTE]
    >  As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts. For more information about how to configure BizTalk Server for high availability, see [Planning for High Availability](../core/planning-for-high-availability3.md).  
  
-   **Master secret server.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).  
  
-   **SQL Server.** Same as the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Domain controller.** Same as in the Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Administration tools.** Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).  
  
## See Also  
 [Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [Sample Scenarios for Threat Model Analysis](../core/sample-scenarios-for-threat-model-analysis.md)
