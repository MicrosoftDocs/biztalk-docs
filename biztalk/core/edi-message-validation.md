---
title: "EDI Message Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71f34561-d280-48bb-b1dd-ce37b87c5023
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Message Validation
EDI data is transmitted as delimited files (without self describing tags) and therefore the encoding rules enforce strict formatting rules to ensure the destination application is able to successfully parse and consume the information for downstream processing.  
  
 The EDI receive pipeline and EDI send pipeline in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 perform a series of validations. Some are always performed; others are performed if enabled in agreement properties or in the schema. For more information about how validation is configured, see [How Validation of an EDI Interchange Is Configured](../core/how-validation-of-an-edi-interchange-is-configured.md).  
  
 Validation of an EDI interchange involves several different kinds of validation, as described in the following topics.  
  
## In This Section  
  
-   [How Validation of an EDI Interchange Is Configured](../core/how-validation-of-an-edi-interchange-is-configured.md)  
  
-   [EDI Structural Validation](../core/edi-structural-validation.md)  
  
-   [Agreement Properties Validation](../core/agreement-properties-validation.md)  
  
-   [EDI Type (Data Element) Validation](../core/edi-type-data-element-validation.md)  
  
-   [Extended (BTS-XSD) Validation](../core/extended-bts-xsd-validation.md)  
  
-   [Schema Validation](../core/schema-validation2.md)  
  
-   [Cross Field-Segment Validation](../core/cross-field-segment-validation.md)