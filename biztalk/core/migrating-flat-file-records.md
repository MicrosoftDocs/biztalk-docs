---
title: "Migrating Flat File Records | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75cd5fbc-66c1-4c8b-b81a-1d028e9647b4
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Migrating Flat File Records
Microsoft [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] and Microsoft [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] support only single character delimiters in flat file records during parsing and serializing. This restriction is offset by greater flexibility in handling delimiters. [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] and [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] also support setting different delimiters on records, fields, and subfields. In contrast, Microsoft BizTalk Server supports multi-character delimiters, although it supports only one type of delimiter—child delimiter. The improvements in delimiter handling may affect how [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] and [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] flat file records are handled in BizTalk Server.  
  
 Three schema annotations control delimiter handling in [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] and [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)], two for parsing (**skip_CR**, **skip_LF**), and one for serializing (**append_newline**). BizTalk Server interprets these annotations as follows when migrating records:  
  
-   If the **skip_CR** annotation has a value of **true** and the current delimiter is not carriage return (0x0D), BizTalk Server adds a carriage return to the current delimiter. For example, if the current delimiter were the pipe symbol (0x7C), the resulting delimiter is a pipe symbol followed by a carriage return (0x7C 0x0D). If the current delimiter is carriage return, it remains as a single carriage return regardless of the value of **skip_CR**.  
  
-   If the **skip_LF** annotation has a value of **true**, BizTalk Server adds a linefeed character (0x0A) to the current delimiter. Notice that in the preceding case where the current delimiter is the pipe symbol (0x7C), a three character delimiter results (0x7C 0x0D 0x0A) if both **skip_CR** and **skip_LF** are **true**.  
  
-   BizTalk Server ignores the setting of the **append_newline** annotation.  
  
 While these interpretations of the annotations ensure the majority of cases migrate without difficulty, there are some cases where migration fails. For example, if **skip_CR** and **skip_LF** are both **true** and the current delimiter is the pipe symbol (0x7C), [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] and [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] accept all of the following as valid delimiters within a single set of records: 0x7C 0x0D 0x0A, 0x7C 0x0D, 0x7C 0x0A, and 0x7C. Records using such sets of delimiters cannot be migrated and require custom parser code in BizTalk Server.  
  
 Although BizTalk Server has only one type of delimiter, it interprets the old annotations so that records migrate easily. If a [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] or [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] schema has values for **def_record_delimdef_field_delim**, **def_subfield_delim**, and these are referenced in **delimiter_type** as **inherit_record**, and so on, BizTalk Server retrieves the corresponding value and stores it locally.  
  
 In addition, BizTalk Server adds fields for tagged positional records without children.  
  
## See Also  
 [Known Issues with Schema Generation and Validation](../core/known-issues-with-schema-generation-and-validation.md)