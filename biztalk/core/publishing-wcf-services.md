---
title: "Publishing WCF Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publishing, WCF services"
  - "WCF services, publishing"
ms.assetid: 70b7851b-77c1-4ab3-a61f-e7165ceb56fb
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Publishing WCF Services
An orchestration can be published as a WCF service in [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to be called by WCF clients.  
  
 **Publishing WCF services with the isolated WCF adapters**  
  
 You create and publish WCF services by using the BizTalk WCF Service Publishing Wizard for the isolated WCF adapters such as the WCF-BasicHttp adapter, the WCF-WSHttp adapter, and the WCF-CustomIsolated adapter. This creates a receive location which exists as an out of process application in IIS.  
  
 Before you publish a WCF service with the isolated WCF adapters, you should have an understanding of how to host WCF services in Internet Information Services (IIS).  
  
 **Publishing service metadata for the WCF receive locations**  
  
 You create service metadata for published WCF receive locations by using the BizTalk WCF Service Publishing Wizard. To generate service model client code from the published metadata documents you can use the Service Model Metadata Utility tool (SvcUtil.exe) included in the [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Software Development Kit (SDK) for [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] and [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Runtime Components.  
  
> [!IMPORTANT]
>  Before running the BizTalk WCF Service Publishing Wizard, you must enable WCF services. For more information about enabling WCF services for your system, see [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).  
  
## In This Section  
  
-   [Publishing WCF Services with the Isolated WCF Receive Adapters](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [Publishing Service Metadata for the WCF Receive Adapters](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)  
  
-   [Considerations When Publishing WCF Services with the WCF Receive Adapters](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)  
  
-   [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md)  
  
-   [How to Throw Fault Exceptions from Orchestrations Published as WCF Services](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)