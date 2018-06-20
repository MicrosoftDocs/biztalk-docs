---
title: "Data Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data types, messages"
  - "messages, data types"
ms.assetid: 7a758289-1629-48a0-843d-6f6773bd5ba6
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Types
The data type specification is an important tool for partitioning the complexity of the HL7 standard, and is critical to understanding the data contents of an HL7 field. Some data types are simple and contain only one component, and some contain many components and subcomponents. For example, PID.5 Patient Name has the data type XPN in Version 2.4. This data type supports the common subdivisions of an English language name, for example, surname, first name, middle name, as well as suffix, prefix, name type code, and name validity (date) range.  
  
 In new HL7 versions, you can add but not remove data types. If you add content to a data type, by adding new components or subcomponents, you can only add them at the end of the structure within which they are nested. In some cases, the HL7 organization merged existing data types to form new ones. This led to the need to support items that were formerly subcomponents within the original data types.  
  
 The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] supports standard data types for all HL7 versions from V2.1 on.  
  
- You can restrict data types where appropriate when developing interfaces.  
  
## In This Section  
  
-   [Data Type ID in HL7 2.1](../../adapters-and-accelerators/accelerator-hl7/data-type-id-in-hl7.md)