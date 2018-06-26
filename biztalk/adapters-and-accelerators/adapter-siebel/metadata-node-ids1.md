---
title: "Metadata Node IDs for the Siebel adapter in BizTalk Adapter Pack | Microsoft Docs"
description: Metadata, search, retrieval nodes types and IDs used in Siebel components that are exposed in Siebel adapter - BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bdffc8d1-0a0a-48d7-b134-5d16acf2c523
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Node types and IDs for the Siebel adapter

## Metadata node types and IDs 
 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces Siebel system artifacts in a hierarchical manner. The following table describes the node types and node IDs for Siebel artifacts surfaced by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  


|                Artifact                 | Node Type |                                 Node Id                                  |                                          Example                                          |                                  Description                                   |
|-----------------------------------------|-----------|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| Business Objects (All Business Objects) | CATEGORY  |                        [VERSION]/BusinessObjects                         |                http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects                |                         Returns all business objects.                          |
|          Business Object (BO)           | CATEGORY  |                      [VERSION]/BusinessObjects/[BO]                      |            http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account            | Returns all business components associated with the specified business object. |
|         Business Component (BC)         | CATEGORY  |                   [VERSION]/BusinessObjects/[BO]/[BC]                    |        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account        |    Returns all operations associated with the specified business component.    |
|                 Insert                  | OPERATION |                [VERSION]/BusinessObjects/[BO]/[BC]/Insert                |    http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert     |       Returns the Insert operation for the specified business component.       |
|                  Query                  | OPERATION |                [VERSION]/BusinessObjects/[BO]/[BC]/Query                 |     http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Query     |       Returns the Query operation for the specified business component.        |
|                 Update                  | OPERATION |                [VERSION]/BusinessObjects/[BO]/[BC]/Update                |    http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Update     |       Returns the Update operation for the specified business component.       |
|                 Delete                  | OPERATION |                [VERSION]/BusinessObjects/[BO]/[BC]/Delete                |    http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete     |       Returns the Delete operation for the specified business component.       |
|                Associate                | OPERATION |              [VERSION]/BusinessObjects/[BO]/[BC]/Associate               |   http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Associate   |     Returns the Associate operation for the specified business component.      |
|               Dissociate                | OPERATION |              [VERSION]/BusinessObjects/[BO]/[BC]/Dissociate              |  http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Dissociate   |     Returns the Dissociate operation for the specified business component.     |
|  Query_[MVG Child Business Component]   | OPERATION | [VERSION]/BusinessObjects/[BO]/[BC]/Query_[MVG Child Business Component] | http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Query_Contact |          Returns the Query operation for the child business component          |
|            Business Services            | CATEGORY  |                        [VERSION]/BusinessServices                        |               http://Microsoft.LobServices.Siebel/2007/03/BusinessServices                |                         Returns all business services.                         |
|            Business Service             | CATEGORY  |              [VERSION]/BusinessServices/[Business Service]               |             http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/ATP              |        Returns all business methods for the specified business service.        |
|         Business Service Method         | OPERATION | [VERSION]/BusinessServices/[Business Service]/[Business Service Method]  |       http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/ATP/ATPRunCheck        |                 Returns the specified business service method.                 |

 [VERSION] = The version string; for example http://Microsoft.LobServices.Siebel/2007/03.  

 [BO] = A Siebel business object; for example, Account.  

 [BC] = A business component; for example, Account.  

 [Business Service] = A Siebel business service; for example, ATP.  

 [Business Service Method] = A method of a business service; for example, DismissAlarm.  

 [MVG Child Business Component] = A multi-value group child business component; for example, Contact.  

## Metadata Search and Node IDs  
 Metadata search is a powerful feature that the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] surfaces as part of its **MetadataRetrievalContract** interface. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] leverages this feature to support searching the following Siebel artifacts.  

|Artifact|Node Id|Description|  
|--------------|-------------|-----------------|  
|Business Object|[VERSION]/BusinessObjects|Return business objects that match the search expression.|  
|Business Component|[VERSION]/BusinessObjects/[BO]|Return business components that match the search expression.|  
|Business Service|[VERSION]/BusinessServices|Return business services that match the search expression.|  
|Business Service Method|[VERSION]/BusinessServices/[Business Service]|Return business service methods that match the search expression.|  

 [VERSION] = The version string; for example http://Microsoft.LobServices.Siebel/2007/03.  

 [BO] = A Siebel Business Object; for example, Account.  

 [Business Service] = A Siebel Business Service; for example, ATP.  

 For valid search expressions, refer to the Siebel documentation.  

> [!NOTE]
>  The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] only supports searches at the level below the currently selected node.  For example, when BusinessObjects is selected, A* is a supported search, but A\*/A\* is not.  

## Metadata Retrieval and Node IDs  
 The Siebel adapter captures the following characteristics for each type of artifact.  

|Artifact|Metadata Characteristics|  
|--------------|------------------------------|  
|Business Component|<ul><li>Business component name</li><li>Business component field names</li><li>Business component field data types mapped to simple/complex WSDL types</li><li>Business component field length mapped to facet maxLength</li><li>Business component mandatory field mapped to facet minOccurs = 1</li><li>Business component optional field mapped to facet minOccurs = 0</li><li>Business component picklist field mapped to a Picklist complex type in WSDL</li><li>Business component static bounded picklist to contain an enumerated list of values</li><li>Business component field NULL constraint mapped to facet isNillable = true</li><li>Business component operations<br /><br /> <ul><li>INSERT</li><li>QUERY</li><li>UPDATE</li><li>DELETE</li><li>ASSOCIATE</li><li>DISSOCIATE</li><li>QUERY_[MVG Child Business Comp] for each child business component with which the business component has an m:n relationship</li></ul></li></ul>|  
|Business Service Method|-   Business Service name<br />-   Method name<br />-   Method is the operation<br />-   Method parameter names<br />-   Method parameter data types mapped to WSDL types<br />-   Method parameter direction mapped to WSDL parameter direction<br />-   Method parameter order mapped to element sequence|  

 For detailed information about the format of the metadata that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes for specific artifacts and operations on the Siebel system, see [Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).  
