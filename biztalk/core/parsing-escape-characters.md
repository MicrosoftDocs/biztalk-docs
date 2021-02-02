---
description: "Learn more about: Parsing Escape Characters"
title: "Parsing Escape Characters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom], code samples"
  - "pipeline components [custom], escape characters"
  - "pipeline components [custom], parsing"
ms.assetid: 2b33f436-3c29-4ff5-8dfa-26d6591713bc
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Parsing Escape Characters
When the parser encounters an escape character that prefixes a regular character (that is, one that is not a delimiter or other special character), the escape character is ignored. For example, given a string "abc\d" where "\\" is the escape character, the output is "abcd".  
  
 If the parser encounters a double escape character (for example, "abc\\\d"), the output includes a single escape character ("abc\d").  
  
 If the parser encounters three escape characters (for example, abc\\\\\d), the output is "abc\d" because the first two escape characters are parsed to "\\" and the third escape character is ignored.  
  
 The parser treats misplaced delimiters as regular characters. For example, if "Record, Field1, Field,2" is received, the output XML is \<Field1\> \<Field,2\>.  
  
## See Also  
 [Using the Flat File Parsing Engine](../core/using-the-flat-file-parsing-engine.md)
