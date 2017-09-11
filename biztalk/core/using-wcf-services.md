---
title: "Using WCF Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF services"
  - "Windows Communication Foundation (WCF)"
ms.assetid: 34fe5e4c-6a92-4627-b2aa-e8b58a708320
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using WCF Services
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides built-in support for Windows Communication Foundation (WCF). [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to reuse and aggregate all your existing WCF services within your orchestrations. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] also implements support for native adapters in WCF services. Native adapter support provides scalability, fault tolerance, and tracking capabilities for WCF services without requiring you to write code. For information about the WCF adapters, see [WCF Adapters](../core/wcf-adapters.md).  
  
 The WCF services support in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] falls into two categories: publishing or creating WCF services, or calling or consuming WCF services.  
  
 **Publishing WCF services**  
  
 You can publish (expose) your orchestrations and schemas as WCF services with the WCF adapters to separate the WCF service logic from the business process logic. For isolated WCF adapters, you can use the BizTalk WCF Service Publishing Wizard to create isolated WCF receive locations hosted by Web applications running in Internet Information Services (IIS). For the in-process WCF adapters, you can publish service metadata for any WCF locations with the BizTalk WCF Service Publishing Wizard.  The publishing of metadata allows the creation of client code using the svcutil.exe utility.  
  
 **Consuming WCF services**  
  
 You can use the BizTalk WCF Service Consuming Wizard to generate the BizTalk artifacts, such as BizTalk orchestrations and types, to consume a WCF service based on the metadata document of the WCF service. Metadata allows a send port to access an external service as a client. Metadata is used purely for describing the endpoint address, binding, and contract.  
  
## In This Section  
  
-   [Publishing WCF Services](../core/publishing-wcf-services.md)  
  
-   [Consuming WCF Services](../core/consuming-wcf-services.md)  
  
-   [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [WCF Adapter Walkthroughs](../core/wcf-adapter-walkthroughs.md)