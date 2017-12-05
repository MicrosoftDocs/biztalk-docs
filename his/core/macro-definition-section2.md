---
title: "Macro Definition Section2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28e11081-56c1-423e-a113-a413720c4339
caps.latest.revision: 4
---
# Macro Definition Section
The macro definition section is bounded by **BEGIN_MACROS** and **END_MACROS** statements and consists of lines with the following syntax.  
  
 *macro_name* **EQU** *control_character_list*  
  
 The macro name can be any alphanumeric string that does not contain spaces, and the control character list consists of one or more two-digit hexadecimal values representing the data to be sent to the printer.  
  
 For example, the following macro defines the NUL character.  
  
```  
NUL EQU 00  
  
```  
  
 For an example macro definition, see [Sample Source Text File](../core/sample-source-text-file1.md).  
  
## See Also  
 [Printer Definition Files](../core/printer-definition-files1.md)