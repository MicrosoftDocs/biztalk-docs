---
title: "Handling Encoding in a Disassembler Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom], encoding"
  - "pipeline components [custom], disassembling"
ms.assetid: 33420357-421f-4ad0-8eee-d445376676db
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Handling Encoding in a Disassembler Pipeline Component
Ensure that your custom disassembler component encodes outbound documents in one of the following formats:  
  
- UTF-8  
  
- UTF-16  
  
- UTF-32  
  
- UTF-16LE  
  
- UTF-16BE  
  
  The orchestration engine may not be able to process documents with other encoding formats.  
  
  UTF-32LE and UTF-32BE are not supported by the .NET Framework; to use these formats, you must create a custom encoding implementation.  
  
## See Also  
 [Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md)