---
title: "Get Metadata Programmatically from SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IMetadataRetrievalContract endpoint"
  - "metadata, retrieving programmatically"
  - "WS-Metadata Exchange (MEX) endpoint"
ms.assetid: 8d75332e-c103-4bd5-a9a2-56d21747a04e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Get Metadata Programmatically from SAP
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is a custom WCF binding that exposes an SAP system as a WCF service. The adapter exposes the SAP system as a self-describing service; that is, a service that is capable of publishing metadata about the operations that it supports. Metadata describes the logical interface to a WCF service; that is, the service contract, messages, and message schemas that must be used to interact with the service.  
  
 This metadata is used by tools such as:  
  
- The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate managed code representations of the service contract, and  
  
- The [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate message schemas.  
  
  However, you can also retrieve metadata programmatically from the adapter. For example, you might want to do this to create a custom metadata retrieval tool to use in an existing application.  
  
  The adapter publishes metadata through two endpoints:  
  
- A WS-Metadata Exchange (MEX) endpoint. WCF automatically provides a MEX endpoint for all WCF bindings. You can use metadata exchange to retrieve metadata for operations supported by the adapter on the underlying SAP system.  
  
- An **IMetadataRetrievalContract** endpoint. The **IMetadataRetrievalContract** interface is implemented by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]. It categorizes SAP system artifacts at multiple logical levels and presents them as a tree of metadata nodes. You can use methods exposed by the **IMetadataRetrievalContract** interface to browse and search the nodes of this tree and to return metadata for operations in which you are interested.  
  
  The topics in this section describe how to use MEX and **IMetadataRetrievalContract** endpoints to retrieve metadata programmatically from the adapter.  
  
## In This Section  
  
-   [Retrieving Metadata Using WS-Metadata Exchange in SAP](../../adapters-and-accelerators/adapter-sap/get-metadata-using-ws-metadata-exchange-in-sap.md)  
  
-   [Retrieving Metadata in SAP Using IMetadataRetrievalContract](../../adapters-and-accelerators/adapter-sap/get-metadata-in-sap-using-imetadataretrievalcontract.md)  
  
## See Also  
[Develop your SAP applications](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)