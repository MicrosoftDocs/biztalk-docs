---
title: "Metadata Node IDs for the mySAP adapter in BizTalk Adapter Pack | Microsoft Docs"
description: Metadata, search, retrieval nodes types and IDs used in SAP components that are exposed in mySAP adapter - BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 46385060-f56a-4e06-9122-b75808776716
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Node Types and IDs for the SAP adapter

## Metadata node types and IDs
The following table lists the node type and node ID for the SAP artifacts that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces. The node ID is the absolute path of the node that is used in the **IMetadataRetrievalContractBrowse**, **Search**, and **GetMetadata** methods.  
  
|Artifact Display Name|Node Type|Node ID|  
|---------------------------|---------------|-------------|  
|RFC|CATEGORY|[VERSION]/RFCSECTION|  
|[RFC_APPL_GROUP_NAME]|CATEGORY|[VERSION]/RFCGROUP/[RFC_APPL_GROUP_ID]|  
|[RFC_NAME]|OPERATION|[VERSION]/Rfc/[RFC_NAME]|  
|RfcGetAttributes|OPERATION|[VERSION]/RfcApi/RfcGetAttributes|  
|TRFC|CATEGORY|[VERSION]/TRFCSECTION|  
|[TRFC_APPL_GROUP_NAME]|CATEGORY|[VERSION]/TRFCGROUP/[TRFC_APPL_GROUP_ID]|  
|[TRFC_NAME]|OPERATION|[VERSION]/TRfc/[TRFC_NAME]|  
|RfcConfirmTransID|OPERATION|[VERSION]/RfcApi/RfcConfirmTransID|  
|BAPI|CATEGORY|[VERSION]/BAPISECTION/000001|  
|[BAPI_APPL_GROUP_NAME]|CATEGORY|[VERSION]/BAPISECTION/[ BAPI_APPL_GROUP_NODE_ID]|  
|[BUSINESS_OBJECT_NAME]|CATEGORY|[VERSION]/BAPIOBJ/[BUSOBJ_TYPE]|  
|[BUSINESS_OBJECT_METHOD]|OPERATION|[VERSION]/BAPIOBJ/[BUSOBJ_TYPE]/[BUSOBJ_METHOD]/[FUNCTION_MODULE]|  
|IDOC|CATEGORY|[VERSION]/IDOCSECTION|  
|[IDOC_MSG_TYPE_NAME]|CATEGORY|[VERSION]/IDOCMESTYP/[IDOC_MSG_TYPE_NAME]|  
|[IDOC_TYPE_NAME] ( [IDOC_CIMTYPE] )|CATEGORY|[VERSION]/IDOCCIMTYP/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[FIRST_IDOC_REL_NO]|  
|[IDOC_TYPE_NAME].V[IDOC_VERSION] ( [IDOC_CIMTYPE] ) ([IDOC_REL_NO])|CATEGORY|[VERSION]/IDOCCIMVER/[IDOC_VERSION]/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[IDOC_REL_NO]|  
|Send|OPERATION|[VERSION]/Idoc/[IDOC_VERSION]/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[IDOC_REL_NO]/Send|  
|SendIdoc|OPERATION|[VERSION]/Idoc/SendIdoc|  
|Receive|OPERATION|[VERSION]/Idoc/[IDOC_VERSION]/[IDOC_TYPE_NAME]/[IDOC_CIMTYPE]/[IDOC_REL_NO]/Receive|  
|ReceiveIdoc|OPERATION|[VERSION]/Idoc/ReceiveIdoc|  
  
 [VERSION] = The version string; for example, http://Microsoft.LobServices.Sap/2007/03.  
  
 [RFC_APPL_GROUP_NAME] = The name of an application group; for example, Sales.  
  
 [RFC_APPL_GROUP_ ID] = The ID associated with an application group in SAP; for example, V (for Sales).  
  
 [RFC_NAME] = The name of an RFC; for example, RFC_GET_SYSTEM_INFO.  
  
 [TRFC_APPL_GROUP_NAME] = The name of an application group; for example, Sales. This is the same of the application group for RFCs.  
  
 [TRFC_APPL_GROUP_ ID] = The ID associated with an application group in SAP; for example, V (for Sales). This is the same as the ID for RFCs.  
  
 [TRFC_NAME]= The name of a tRFC; for example, RFC_GET_SYSTEM_INFO. This is the same as the RFC name.  
  
 [BAPI_APPL_GROUP_NAME] = The name of the BAPI group as in the BAPI explorer in SAP. For example, Sales and Distribution.  
  
 [BAPI_APPL_GROUP_NODE_ID] = The ID associated with the corresponding node in the BAPI explorer tree in SAP; For example, 3253 for Sales and Distribution. Note that there could be more group nodes under a given BAPI group node. For example, the Sales and Distribution node has another group node under it called Sales (node ID 3375).  
  
 [BUSINESS_OBJECT_NAME] = The name of a business object; for example, Sales Order.  
  
 [BUSOBJ_TYPE] = The business object type in SAP; for example BUS2032 for the Sales Order business object.  
  
 [BUSINESS_OBJECT_METHOD] = The name of a business object method; for example, GETLIST for the Sales Order business object.  
  
 [FUNCTION MODULE] = The SAP function module for the business object method; for example, BAPI_SALESORDER_GETLIST for GETLIST method of the Sales Order business object.  
  
 [IDOC_MSG_TYPE_NAME] = The name of an IDOC message type; for example, ORDERS.  
  
 [IDOC_TYPE_NAME] = The name of the IDOC type; for example, ORDERS05.  
  
 [IDOC_CIMTYPE] = The IDOC CIM Type (extension); for example, Z1ORDERS.  
  
 [FIRST_IDOC_REL_NO] = The minimum IDOC release number for a particular IDOC type; for example, 46A for ORDERS05 in a particular SAP system.  
  
 [IDOC_VERSION] = The IDOC release version number; 2 for release 2 IDOCS and 3 for release 3 IDOCS..  
  
 [IDOC_REL_NO] = The IDOC release number; for example 46A, 46B, or 620.  
  
## Metadata Search Node IDs  
 Metadata search is a powerful feature that the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] surfaces as part of its **IMetadataRetrievalContract** interface. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses this feature to support searching the following SAP artifacts.  
  
|Artifact Display Name|Node ID|Description|  
|---------------------------|-------------|-----------------|  
|/RFC|[VERSION]/RFCSECTION|Return all RFC operations that match the search expression.|  
|/RFC/[RFC_APPL_GROUP_NAME]|[VERSION]/RFCGROUP/[RFC_APPL_GROUP_NAME]|Return RFC operations in the application group that match the search expression.|  
|/TRFC|[VERSION]/TRFCSECTION|Return all RFC operations that match the search expression.|  
|/TRFC/[TRFC_APPL_GROUP_NAME]|[VERSION]/TRFCGROUP/[TRFC_APPL_GROUP_NAME]|Return RFC operations in the application group that match the search expression.|  
|/BAPI|[VERSION]/BAPISECTION|Return all BAPIs that match the search expression.|  
|/IDOC|[VERSION]/IDOCSECTION|Return all IDOCs that match the search expression.|  
  
 The following table lists the wildcard characters that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports in search expressions.  
  
|Special Character|Interpretation|  
|-----------------------|--------------------|  
|plus (+)|Matches exactly one character.<br /><br /> For example, A+ matches AB, AC, AD, and so on.|  
|asterisk (*)|Matches zero or more characters; for example, “A*” matches “A”, “AB”, “ABC”, and so on.|  
  
## Metadata Retrieval Node IDs  
 The following table summarizes the metadata characteristics returned by [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
|Artifact|Metadata Characteristics|  
|--------------|------------------------------|  
|RFC|-   RFC name.<br />-   RFC import, export, changing and table parameters.<br />-   RFC parameter data types.<br />-   RFC parameter field length mapped to facet maxLength<br />-   RFC mandatory parameter mapped to facet minOccurs = 1<br />-   RFC optional parameter mapped to facet minOccurs = 0<br />-   RFC parameter NULL constraint mapped to facet isNillable = true. This means that the adapter should not pass this parameter to the SAP system.<br />-   The RFC itself is the operation.|  
|TRFC|Same as RFC except<br /><br /> -   RFC import parameters are not surfaced. Because tRFC is asynchronous, no output parameters are surfaced.|  
|BAPI|-   Name of business object<br />-   Name of business object method<br />-   Same as RFC characteristics|  
|IDOC|IDOC Type<br /><br /> CIMType<br /><br /> IDOC release number<br /><br /> IDOC version<br /><br /> IDOC control record fields mapped to an EDI_DC complex type<br /><br /> IDOC data record segments and segment fields mapped to an EDI_DD complex type<br /><br /> Segment parent-child relationships<br /><br /> IDOC segment mandatory parameter mapped to minOccurs  = 1<br /><br /> IDOC segment optional parameter mapped to minOccurs  = 0<br /><br /> IDOC segment header field name<br /><br /> IDOC segment header field data type<br /><br /> IDOC segment field name<br /><br /> IDOC segment field data type<br /><br /> IDOC segment field value enumerations<br /><br /> IDOC segment field min, max values (ranges) **Note:**  When an IDOC segment field contains a list of min values, it is surfaced as an enumeration. If the IDOC segment field contains both min and max values, it is surfaced as a string without any enumeration or range constructs.|  
  
 For detailed information about the format of the metadata that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes for specific artifacts and operations on the SAP system, see [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).  
  
