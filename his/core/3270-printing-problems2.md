---
title: "3270 Printing Problems2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81d9cf81-6c93-4af2-a821-81105612ff65
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# 3270 Printing Problems
The 3270 datastream was not designed for proportional fonts. This can cause problems in some print jobs, resulting in characters that overlap. The advanced settings of the Print Server Properties page allows you to configure Host Print Service to use a different method of positioning characters.  
  
 **Problems with Form Feeds**  
  
 One commonly seen problem with Host Print Service is extra or missing form feeds (FF). Some of these issues involve how SNA Print handles explicit form feeds. Other issues relate to using the number of lines per page, in place of a FF character, to cause a page break (form feed).  
  
 When Host Print Service receives a FF character in the host data stream ('0x0C'), it holds this character until it receives additional data, either control codes (SCS or 3270 orders) or printable characters. If it receives additional data, the FF is sent to the printer and the additional data is processed. If no further data is received, meaning we are at the end of the job, the FF is dropped. At this point the SNA Print will complete the outstanding job by calling either **EndDoc** for sessions not using a PDT or **EndDocPrinter**, for sessions using a PDT. When **EndDoc** is called, a FF is added to the end of the job. When **EndDocPrinter** is called, no FF is added. In this latter case, whether SNA Print adds a FF to the end of the job depends on how the END_JOB parameter is configured in the PDT. An alternative to using the PDT is to change the default data type for the print processor in the Windows Printer properties. If the default data type is set to RAW [auto FF], the print driver checks for the presence of a FF and adds one if necessary.  
  
 It is possible to force SNA Print to not drop the final FF when using a PDT. This requires the Registry entry FlushFF be added and set to TRUE.  
  
```  
FlushFF:  REG_SZ   
   HKEY_LOCAL_MACHINE  
     SYSTEM  
       CurrentControlSet  
          Services  
             SnaPrint  
               Parameters  
  
```  
  
|FF at End of Job|PDT|FF added|End results|  
|----------------------|---------|--------------|-----------------|  
|Yes|No|Yes|FF|  
|No|No|Yes|FF|  
|Yes|Yes|No|(depends on PDT)|  
|No|Yes|No|(depends on PDT)|  
  
 Many older host print jobs rely on the number of lines per page to determine page breaks. They assume for example that a job will use 66 lines per page, so add enough blank lines after the text to bring the total number of lines to 66 before starting the text that should be on the next page. If there were 30 lines of text, 36 blank lines would be added before the text intended for the next page. The drawback of this method is it depends on the printable area of the printer, the lines per inch, the lines per page, and the top margin set for the job. If by default only 65 lines will fit per page, the resulting printout will show "page creep," where the last blank line is pushed to the top of the next page, and then two lines to the top of the third page, and so on. This "page creep" can be remedied within the PDT file by having the START_JOB parameter set the top margin to zero and the lines per page to 66. In addition the Printer Session properties should have the lines per inch set to 6.  
  
 For example with a printer using HP PCL the following would be added to the PDF:  
  
 In the macros section:  
  
```  
TOP    EQU 1B 26 6C 30 45    /* Top Margin set to 0 */  
STL    EQU 1B 26 6C 36 36 46        /* Set Text Length to 66 */  
  
```  
  
 For Start Job  
  
```  
START_JOB = TOP0 STL  
  
```  
  
 Host Print Service is designed to execute a form feed (FF) included in an LU 3 print job when any of the following conditions are met:  
  
- If the FF is inserted as the first character after the WCC in a 3270 Erase/Write or Erase/Write Alternate command.  
  
- If the FF is located after a valid NL (New Line) order.  
  
- If the FF is located after the last printable character position of any print line.  
  
  A registry entry is available that will force Host Print Service to honor all form feed characters in an LU 3 print job, even if they do not meet the above conditions. To add this entry, find the following key using Regedit.exe:  
  
```  
HKEY_LOCAL_MACHINE  
   SYSTEM  
    CurrentControlSet  
      Services  
        SnaPrint  
          Parameters  
  
```  
  
 Add the following entry to this key:  
  
```  
Value Name:    
Data Type:    
String:    
```  
  
 **DoAllLU3FFs** should be set to **TRUE**. The system checks to see if this registry entry exists. Any value entered for the string will enable this feature.