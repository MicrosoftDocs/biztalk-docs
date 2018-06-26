---
title: "Browse, search, and get SAP metadata | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "metadata"
  - "adapters, surfacing metadata"
  - "TRFC"
  - "RFC"
  - "metadata, browsing, searching, retrieving"
  - "adapters, operations"
  - "BAPI"
  - "IDOC"
ms.assetid: 5f0d7c1f-d6e1-4c56-8d8e-1f5d537aa3ce
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Browse, search, and get SAP metadata
The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces metadata from the SAP system. This metadata describes the message structure for communicating with an SAP system using the adapter. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports two interfaces for retrieving metadata.  
  
- **MetadataExchange** provided by [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. WCF provides a metadata-exchange endpoint for all WCF bindings, which enables clients to get metadata from the SAP system.  
  
- **IMetadataRetrievalContract** provided by the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], which supports the metadata browsing and searching capabilities of the adapter.  
  
  One of the goals of the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is to expose the SAP system as a WCF service. The adapter surfaces the SAP artifacts (RFCs, BAPIs, and IDOCs) as operations that adapter clients can invoke. The adapter also surfaces some specific operations that can be used to send or receive IDOCs from an SAP system. These operations are listed later in this topic.  
  
  It is possible to browse, search, and retrieve metadata by using the WCF service model, by using the WCF channel model, or by creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
  When using the WCF service model, you must use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate the proxy classes for performing operations on the SAP system. When using a BizTalk project, you must use the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to generate metadata for the operations that you want to perform on the SAP system.  
  
  For more information about browsing, searching, and retrieving metadata using [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], see [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md).  
  
## Browsing Metadata  
 The[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] enables adapter clients to browse the RFCs, tRFCs, BAPIs, and IDOCs exposed by the SAP system. As part of the metadata browse operation, the adapter surfaces the RFCs and BAPIs as operations. For IDOCs, the adapter surfaces operations for sending and receiving IDOCs. These operations are available from [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)],   [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. The SAP metadata is categorized under the following nodes:  
  
- **RFC**. This node contains the RFCs exposed by the SAP system and represents a function module in SAP. The adapter categorizes the RFCs into multiple logical levels and exposes a hierarchical view to the adapter clients. An RFC is at the lowest level of this hierarchy and is exposed as an operation that can be invoked by an external application. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the RFC SDK to generate metadata for the RFCs. The adapter can invoke only those RFCs for which it can generate the metadata.  
  
   Other than surfacing the RFCs as operations, the adapter also surfaces some specific operations such as **RfcGetAttributes**. For more information about these operations, see [Operations on RFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md).  
  
- **TRFC**. This node contains the tRFCs exposed by the SAP system. tRFCs are not a conventional artifact in an SAP system, but rather a mechanism to invoke RFCs. tRFCs are categorized under a separate node because their metadata characteristics are different from RFCs. Specifically, RFCs also include export parameters. The adapter categorizes the tRFCs into multiple logical levels and exposes a hierarchical view to the adapter clients. A tRFC is at the lowest level of this hierarchy and is exposed as an operation that can be invoked by an external application.  
  
   Other than surfacing the tRFCs as operations, the adapter also surfaces some specific operations such as **RfcConfirmTransID**. For more information about these operations, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).  
  
- **BAPI**. This node contains the BAPIs exposed by the SAP system. The adapter categorizes the BAPIs into multiple logical levels and exposes a hierarchical view to the adapter clients. A BAPI is at the lowest level of this hierarchy and is exposed as an operation that can be invoked by an external application.  
  
- **IDOC**. This node contains the IDOCs exposed by an SAP system. The adapter categorizes the IDOCs into multiple logical levels and exposes a hierarchical view to the adapter clients. The operations that the adapter exposes for the IDOCs are:  
  
  - **Send** and **Receive**. Adapter clients can use these operations to send and receive IDOCs from an SAP system using a strongly-typed schema.  
  
  - **SendIdoc** and **ReceiveIdoc**. Adapter clients can use these operations to send and receive IDOCs from an SAP system using a weakly-typed schema.  
  
    For more information about these operations, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).  
  
  For more information about how metadata is categorized, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
## Searching Metadata  
 In the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], adapter clients can search metadata in an SAP system by using search expressions that are dependent on the underlying RFCs that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses. The following table lists the SAP artifacts and the metadata hierarchy under which adapter clients can search.  
  
|Artifact|Searches under the node in GUI|  
|--------------|------------------------------------|  
|RFC|-   /RFC<br />-   /RFC/[Application Group]|  
|tRFC|-   /TRFC<br />-   /TRFC/[Application Group]|  
|BAPI|-   /BAPI|  
|IDOC|-   /IDOC|  
  
 The following table lists the special characters that can be used for search and their interpretation by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
|Special character|Interpretation|  
|-----------------------|--------------------|  
|+ (plus)|Matches exactly one character.<br /><br /> For example, A+ matches AB, AC, AD|  
|* (asterisk)|Matches zero or more characters.<br /><br /> For example, A* matches A, AB, ABC.|  
  
## Retrieving Metadata  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] enables adapter clients to retrieve metadata for the SAP system, including detailed metadata characteristics:  
  
- For an RFC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retrieves the RFC name along with import, export, changing, and table parameters. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] also retrieves the data types for parameters, field length of parameters, in addition to mandatory and optional parameters.  
  
- For a tRFC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retrieves details similar to the RFC, with the exception of export parameters. Because tRFC calls are asynchronous, no output parameters are retrieved.  
  
- For a BAPI, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retrieves the business object name, business object method name, and other specific information similar to RFCs.  
  
- For an IDOC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] retrieves the IDOC type, the release number, the version, IDOC control records, IDOC data records, and other IDOC segment information.  
  
  > [!NOTE]
  >  If metadata for IDOC contains both low and high values (range) for a data type, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes that as a string. If the metadata contains only low values, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes that as an enum.  
  
> [!NOTE]
>  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes the SAP function parameters in an alphabetical order, irrespective of how the parameters are ordered in the SAP function definition. This is because of the following reasons:  
> 
> - Different versions of SAP RFC SDK return SAP function parameters in different orders. Hence, in order to provide a consistent experience to the adapter users, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes the parameters in an alphabetical order.  
>   - Same RFCs on different SAP servers could have different order of exposing function parameters. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] makes this difference transparent to the users by exposing the parameters in a consistent alphabetical order.  
> 
> [!NOTE]
>  While retrieving data from the SAP system using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not deserialize messages having more than 65536 nodes. Make sure the response message has nodes less than or equal to 65536. You can work around this limitation by modifying the app.config file for your application. For instructions, see [Troubleshoot Operational Issues](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md).  
  
 For more information about browsing, searching, and retrieving metadata, see [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md).  
  
## See Also  
 [Architecture overview of BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)