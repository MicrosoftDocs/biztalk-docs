---
title: "RosettaNet PIPs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PIPs, clusters"
  - "RosettaNet, PIPs"
  - "PIPs, PIP specifications"
  - "PIPs, segments"
  - "PIPs, RosettaNet"
  - "DTDs, DTD files"
ms.assetid: 2f7e8db3-9ccb-403a-9fe7-58fbba3c4cb1
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# RosettaNet PIPs
The RosettaNet organization creates and maintains Partner Interface Processes (PIPs) to provide common business-process definitions for all RosettaNet message exchanges.  
  
 Each PIP specification provides a document type definition (DTD) file and a message guideline document. The DTD file defines the service-content message structure. The message-guideline document, which is a human-readable HTML file, specifies element-level constraints. Together, they provide a complete definition of the business process.  
  
 For more information about PIP specifications, see the RosettaNet Web site at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859).  
  
## PIP Contents  
 A PIP specification does the following:  
  
- Describes which public process pattern it implements  
  
- Describes how to configure the public process  
  
- Provides references to the documents to exchange within the PIP  
  
  A PIP specification includes three major parts: a Business Operational View (BOV), Functional Service View (FSV), and an Implementation Framework View (IFV). Each of these views specifies element-level constraints:  
  
- The BOV specifies the semantics of business data entities and the business process flow. It describes start and end states, and partner roles. It describes the interaction between roles, and details security, audit, and process controls. It specifies the business documents and business data entities.  
  
- The FSV specifies network component services, agents, and interactions. It provides the network component design required to run the PIPs, and describes possible network component interactions.  
  
- The IFV specifies the network-protocol message formats and communication requirements required to run the PIP.  
  
## Clusters and Segments  
 You categorize PIPs by a high-level business function (cluster) and a subfunction (segment). Clusters and segments organize business messages into recognizable categories. The following table lists these clusters and segments.  
  
|Clusters|Segments|  
|--------------|--------------|  
|0: RosettaNet Support|0A: Administrative<br /><br /> 0C: Testing|  
|1: Partner Product & Service Review|1A: Partner Review<br /><br /> 1B: Product & Service Review|  
|2: Product Information|2A: Preparation for Distribution<br /><br /> 2B: Product Change Notification<br /><br /> 2C: Product Design Information<br /><br /> 2D: Collaborative Design & Engineering|  
|3: Order Management|3A: Quote & Order Entry<br /><br /> 3B: Transportation & Distribution<br /><br /> 3C: Returns & Finance<br /><br /> 3D: Product Configuration|  
|4: Inventory Management|4A: Collaborative Forecasting<br /><br /> 4B: Inventory Allocation<br /><br /> 4C: Inventory Reporting<br /><br /> 4D: Inventory Replenishment<br /><br /> 4E: Sales Reporting<br /><br /> 4F: Price Protection|  
|5: Marketing Information Management|5A: Lead Opportunity Management<br /><br /> 5B: Marketing Campaign Management|  
|6: Service and Support|6A: Provide and Administer Warranties, Service Packages, and Contract Services<br /><br /> 6B: Provide and Administer Asset Management (Merged with 6A)<br /><br /> 6C: Technical Support and Service Management|  
|7: Manufacturing|7A: Design Transfer<br /><br /> 7B: Manage Manufacturing WO & WIP<br /><br /> 7C: Distribute Manufacturing Information|  
  
 Each segment includes a number of specific message PIPs. For example, the 3A4 PIP is a part of the Order Management cluster (Cluster 3) and the Quote and Order Entry segment (Segment A of Cluster 3). This segment includes other related message PIPs, as follows:  
  
 Cluster 3: Order Management  
  
-   Segment A: Quote and Order Entry  
  
    -   PIP 3A1: Request Quote  
  
    -   PIP 3A2: Request Price and Availability  
  
    -   PIP 3A3: Request Shopping Cart Transfer  
  
    -   PIP 3A4: Manage Purchase Order  
  
    -   PIP 3A5: Query Order Status  
  
    -   PIP 3A6: Distribute Order Status  
  
    -   …  
  
## See Also  
 [RosettaNet and CIDX Messaging Standards](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md)   
 [RNIF Standard](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)