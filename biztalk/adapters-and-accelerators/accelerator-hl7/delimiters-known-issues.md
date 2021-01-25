---
description: "Learn more about: Delimiters Known Issues"
title: "Delimiters Known Issues | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "known issues, delimiters"
  - "delimiters"
ms.assetid: 4eaacb3c-9d8d-43da-91dd-8bb25dec70e1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Delimiters Known Issues
This section contains useful information that may help you avoid delimiter errors.  
  
## Characters not recommended to be used as delimiters  
 It is recommended that you do not use the following characters as delimiters as they might cause errors:  
  
-   Null characters  
  
-   Spaces  
  
## Extra delimiters in a header or body field cause multiple errors  
 When you have an extra delimiter in a field in an HL7 V2.X message, the Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) parser might generate two error messages, one related to XML validation and the other related to structural validation.  
  
## Trailing delimiters permitted in HL7 batch segments  
 HL7 defined batch segments such as FHS, BHS, BTS, and FTS can have trailing delimiters and are not constrained by the trailing delimiter flag, because [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not validate trailing delimiters for batching segments.  
  
## See Also  
 [Known Issues](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)
