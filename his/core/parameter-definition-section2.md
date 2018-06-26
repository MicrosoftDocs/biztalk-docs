---
title: "Parameter Definition Section2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60b3c7ca-9c63-4a0a-a09c-93d1d2202ad5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Parameter Definition Section
The parameter definition section immediately follows the macro definition section and consists of one or more lines with the following syntax.  
  
 *parameter_name* **=** *value_list*  
  
 The parameter name can be any character string that does not contain spaces. The compiler ignores parameter names not supported by Host Print service.  
  
 The value list can be empty or can contain one or more of the following:  
  
- A three-digit decimal value.  
  
- A two-digit hexadecimal value.  
  
- A one-char character value.  
  
- The name of a macro specified in the macro definition section.  
  
  For example, the following shows a parameter defining the control sequence to be sent to the printer to begin a new line.  
  
```  
NEW_LINE = CRR LFF  
  
```  
  
 In this example, CRR and LFF are the names of macros specified in the macro definition section.  
  
 Host Print service currently supports the following parameters (definitions of unsupported parameters are ignored).  
  
|Parameter name|Description|  
|--------------------|-----------------|  
|START_JOB|Control sequence to be sent at the start of a print job.|  
|END_JOB|Control sequence to be sent at the end of a print job.|  
|CARRIAGE_RETURN|Control sequence for a carriage return.|  
|LINE_FEED|Control sequence for a line feed.|  
|FORM_FEED|Control sequence for a form feed.|  
|NEW_LINE|Control sequence for a new line.|  
|SET_6_LINES_PER_INCH|Control sequence to specify 6 LPI.|  
|SET_8_LINES_PER_INCH|Control sequence to specify 8 LPI.|  
|START_HIGHLIGHT_INTENSE|Control sequence to begin bold printing.|  
|END_HIGHLIGHT_INTENSE|Control sequence to end bold printing.|  
|START_HIGHLIGHT_UNDERLINE|Control sequence to begin underline printing.|  
|END_HIGHLIGHT_UNDERLINE|Control sequence to end underline printing.|  
|KANJI_CODE?|Control sequence of Kanji code for a printer, either JIS or SHIFT_JIS.|  
|KANJI_ON|Control sequence to start printing Kanji.|  
|KANJI_OFF|Control sequence to end printing Kanji.|  
|SET_PAGE_LENGTH|Control sequence to set number of lines per page.|  
|LEFT_MARGIN|Control sequence to set left margin in number of characters.|  
|RIGHT_MARGIN|Control sequence to set right margin in number of characters.|  
|TOP_MARGIN|Control sequence to set top margin in number of lines.|  
|SET_HORIZONTAL_POSITION|Control sequence to set row position.|  
|SET_VARIABLE_LINE_DENSITY|Control sequence to set line density.|  
|SET_VARIABLE_PRINT_DENSITY|Control sequence to set number of characters per inch.|  
|SET_FONT_SIZE|Control sequence to set font size in points.|  
  
## See Also  
 [Printer Definition Files](../core/printer-definition-files2.md)