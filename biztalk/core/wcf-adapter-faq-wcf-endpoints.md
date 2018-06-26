---
title: "WCF Adapter FAQ: WCF Endpoints | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ccc94b7d-b8a6-4c24-907e-922fd885b874
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapter FAQ: WCF Endpoints
## What are two endpoints options can be created by the BizTalk WCF Service Publishing Wizard?  
 When running the BizTalk WCF Service Publishing Wizard, you can select to create either a WCF service endpoint or a WCF metadata-only endpoint (MEX).  
  
 A service endpoint creates an actual Web location hosted in IIS that exposes the functionality of an actual WCF service. Only isolated adapters (WCF-WsHttp, WCF-BasicHttp, and WCF-CustomIsolated) can be used for service endpoints. The functionality of this type of endpoint is implemented by an orchestration or a schema that is published as a WCF service.  
  
 A metadata-only endpoint is one whose functionality is implemented through a BizTalk receive location.  This uses IIS and an in-process WCF receive adapter rather than by an exposed orchestration or actual WCF service code. Using the wizard to generate a metadata-only endpoint is an easier way to provide integration information on exposed receive locations using an in-process WCF adapter than doing it manually using svcutil.exe. Using svcutil.exe forces you to find a way to forward the metadata to the consumer of your service so it can be called.  
  
## Why would I use a metadata-only endpoint in BizTalk Server?  
 With metadata-only endpoints, the service implementation does not exist in an actual WCF service. Rather, the functionality is implemented in a BizTalk receive location, which is called just as a WCF service with a service endpoint. For example, you could have two schemas and a map to take a field in a message and convert it to all uppercase. In this case the service is published in metadata as “ConvertToUpper”. But the functionality of the service is implemented in the receive location and not in code or through an orchestration.  
  
 A WCF endpoint is composed of an address, a binding, and a contract. When the wizard creates a metadata-only endpoint, it gets the address and binding details from the already existing receive location. The contract information is defined by schemas which can exist in a BizTalk orchestration, or you can create them manually using the wizard. If you choose **Publish BizTalk orchestrations as a WCF service**, the metadata-only endpoint uses the message and port types from the orchestration assembly to define the contract.  
  
 If you choose **Publish schemas as WCF service**, the wizard allows you to define a service definition by specifying service and operation names with existing input and output schemas. The wizard creates an .svc file and an IIS virtual directory so the metadata can be browsed after it is published. The BizTalk WCF Service Publishing Wizard also creates a web.config file with its httpGetEnabled attribute of the \<serviceMetadata\> element set to true. This publishes the metadata for browsing. If you choose to publish service metadata for a BizTalk receive location, that data can be accessed through a GET request over HTTP using a `?wsdl` at the end of the URL for the service.  
  
## Are service endpoints hosted in IIS and why?  
 Yes, a service endpoint is hosted in IIS using one of the three isolated adapters:  
  
- WCF-WsHttp  
  
- WCF-BasicHttp  
  
- WCF-CustomIsolated  
  
  A service endpoint differs from a metadata-only endpoint in that its functionality can be called directly as a WCF service. Using the BizTalk WCF Service Publishing Wizard to create a service endpoint results in a new receive location in the specified BizTalk application. It defines a URI at which the orchestration can be accessed through IIS.  
  
## When creating a service endpoint, why would I select to “Publish schemas as a WCF Service”?  
 Choose to publish schemas as a WCF service if your WCF receive location is part of a BizTalk application that is using BizTalk messaging only. This means there are no orchestrations being used, and all the functionality will be exposed through the receive location and send ports. Schemas are published to specify the contract information. This information can be obtained from a schema assembly, or even from an orchestration assembly (although the orchestration may not be used for this endpoint).