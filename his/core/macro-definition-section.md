---
title: "Macro Definition Section1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eddbf6b6-765c-4c17-a628-df04abe0a720
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Macro Definition Section
The macro definition section is bounded by **BEGIN_MACROS** and **END_MACROS** statements and consists of lines with the following syntax.  
  
 *macro_name* **EQU** *control_character_list*  
  
 The macro name can be any alphanumeric string that does not contain spaces, and the control character list consists of one or more two-digit hexadecimal values representing the data to be sent to the printer.  
  
 For example, the following macro defines the NUL character.  
  
```  
NUL EQU 00  
  
```  
  
 For an example macro definition, see [Sample Source Text File](../core/sample-source-text-file.md).  
  
## See Also  
 [Printer Definition Files](../core/printer-definition-files.md)