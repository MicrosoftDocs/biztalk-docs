---
title: "Code Page Specification for Flat File Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 825e75f1-893c-4c61-b566-f893d732a907
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Code Page Specification for Flat File Schemas

## Overview
The value in the **Code Page** property is used to create an encoding object that is used during the disassembly and assembly of flat file documents. This encoding object allows the flat file parser to convert the native encoding of an inbound flat file document into the normalized UTF-8 encoding that is used internally by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The encoding object also allows the flat file serializer to convert the internal UTF-8 encoding back into the native encoding of the flat file document.  
  
 The setting of the **Code Page** property plays an important, but not exclusive, role in determining the character encoding scheme used by your flat file business documents. You must consider how inbound flat file messages are interpreted by the flat file disassembler as well as how the flat file assembler will encode characters as outbound messages are translated into flat file format.  

## Character encoding  
 There are multiple factors that play a role in determining how character encoding for a given instance message is handled, as follows:  
  
-   When disassembling a flat file instance message, the following algorithm is used to determine and preserve encoding information:  
  
    1.  If the **Charset** in the Message body part is set, its value is used.  
  
    2.  Otherwise, if the envelope (or document) schema specifies a code page using the **Code Page** property, its value is used.  
  
    3.  Otherwise, if a byte order mark is present, its value is used.  
  
    4.  Otherwise, assume UTF-8.  
  
-   When assembling a flat file instance message, the following algorithm is used to determine the character set to use for decoding:  
  
-   If the **XMLNorm.TargetCharset** message context property is set, its value is used.  
  
-   Otherwise, if the **TargetCharset** assembler (design-time) property is set, its value is used.  
  
-   Otherwise, if the envelope (or document) schema specifies a code page using the **Code Page** property, its value is used.  
  
    1.  Otherwise, if the **SourceCharset** message context property is set, its value is used.  
  
    2.  Otherwise, use UTF-8.  
  
## See Also  
 **Considerations When Creating Flat File Message Schemas** and **Code Page (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]