---
title: "Minimum Field Lengths Within Delimited Records | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24272d0d-34c8-487a-9334-683c65c159b8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Minimum Field Lengths Within Delimited Records
By definition, the fields in positional records are all defined to have specific exact lengths. Fields in delimited records can also be defined to have a minimum length. This characteristic is defined by the **[Minimum Length with Pad Character** property of **Field Element** and **Field Attribute** nodes.  

 When you provide a nonzero value for the **Minimum Length with Pad Character** property, the flat file assembler will determine whether the number of data characters associated with the field is smaller than the setting of the **Minimum Length with Pad Character** property, the relevant pad character will be used to make up the difference.  

 The pad characters will be added before or after the data characters based on the setting of the **Justification** property for the field. When the **Justification** property is set to **Left**, any pad characters required to meet the minimum length will be added after the data characters. When the **Justification** property is set to **Right**, any pad characters required to meet the minimum length will be added before the data characters.  

 When you provide a nonzero value for the **Minimum Length with Pad Character** property, the flat file disassembler will examine the beginning or end (based on the setting of the **Justification** property) of the field value for the presence of the relevant pad character, and if present, the pad characters will be discarded and not appear in the equivalent XML message being constructed.  

## See Also  
- [Field Considerations](../core/field-considerations.md)   
- **Justification (Node Property of Flat File Schemas)** and **Minimum Length with Pad Character (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
