---
title: "Browse, search, and get Siebel metadata | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "metadata, retrieving"
  - "metadata, surfacing"
  - "retrieving, metadata"
  - "metadata, browsing"
  - "browsing, metadata"
  - "metadata, searching"
  - "searching, metadata"
ms.assetid: 48fc3bb1-b949-4b8d-ab62-a41cd8c2f0a0
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Browse, search, and get Siebel metadata
The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces metadata from the Siebel system that describes the message structure for communicating with a Siebel system using the adapter. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports two interfaces for retrieving metadata.  
  
- MetadataExchange provided by [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. WCF provides a metadata-exchange endpoint for all WCF bindings, which enables clients to get metadata from the Siebel system.  
  
- IMetadataRetrievalContract provided by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], which supports the metadata browsing and searching capabilities of the adapter.  
  
  The goal of the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] is to expose the Siebel system as a WCF service. The adapter surfaces Siebel artifacts (business objects and business services) as operations that adapter clients can invoke.  
  
  Adapter clients can browse, search, and retrieve metadata by using the WCF service model, by using the WCF channel model, or by creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. When using the WCF service model, you must use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the proxy classes for performing operations on the Siebel system. When using a BizTalk project, you must use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate metadata for the operations that you want to perform on the Siebel system. For more information about browsing, searching, and retrieving metadata using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], see [Get Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).  
  
## Browsing Metadata  
 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] enables adapter clients to browse the business objects and business services exposed by the Siebel system. As part of the metadata browse operation, the adapter categorizes the artifacts into multiple logical levels and exposes a hierarchical view of metadata to the adapter clients. Metadata from a Siebel system is categorized under the following nodes:  
  
- **Business Objects**. This node contains the business objects in a Siebel system, which is a logical collection of business components. The business objects are further categorized as business components. At the lowest level of the hierarchy are the operations that you can invoke on the business components.  
  
- **Business Services**. This node contains the business services exposed by a Siebel system. A Siebel business service is a collection of business service methods or functions that can be directly invoked in the Siebel system.  
  
  For more information about how the metadata is categorized, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).  
  
## Searching Metadata  
 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] enables adapter clients to search metadata in a Siebel system. It does this by using valid Siebel search expressions compatible with Siebel’s LIKE operator on the [Name] field of the Siebel repository business component used for metadata browsing. The following table lists the Siebel artifacts and the metadata hierarchy under which they can search.  
  
|Artifact|Searches under the node in the GUI|  
|--------------|----------------------------------------|  
|Business Object|/Business Objects|  
|Business Component|/Business Objects/Business Object Name|  
|Business Service|/Business Services|  
  
 The following table lists the special characters that can be used for search and their interpretation by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
|Special character|Interpretation|  
|-----------------------|--------------------|  
|? (question mark)|Matches exactly one character.<br /><br /> For example, A? matches AB, AC, AD|  
|* (asterisk)|Matches zero or more characters.<br /><br /> For example, A* matches A, AB, ABC.|  
  
## Retrieving Metadata  
 When retrieving metadata, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] can extract metadata under a schema, including all or a subset of business objects or business services with the respective operation parameters. It presents the entities from the Siebel system as element names in XML. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] enables adapter clients to retrieve metadata for the Siebel system, including detailed metadata characteristics:  
  
- For business components, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] retrieves such items as the business object name, business component name, the field names, data types, field lengths, mandatory field, optional field, and picklist field. The adapter also retrieves the operations possible on the business component such as INSERT, UPDATE, DELETE, and QUERY.  
  
- For business service methods, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] retrieves such items as the business service name, the method name (same as operation), method parameters, and parameter data types.  
  
  For more information about retrieving the metadata, see [Get Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).  
  
## See Also  
 [Overview of BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)