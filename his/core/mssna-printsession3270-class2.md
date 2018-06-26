---
title: "MsSna_PrintSession3270 Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16da1be6-9957-461c-a8d5-146ca218673d
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_PrintSession3270 Class
Extends a print session.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_PrintSession3270 : MsSna_PrintSession  
{  
   sint16 JobTermination;  
   sint16 JobTimeoutSecs;  
   boolean JobTimeout;  
   boolean UseGDI;  
   boolean TRNisASCII;  
   boolean CustomTRN;  
   sint32 CustomTRNChar;  
   String LUName;  
   boolean MonitorJob;  
   boolean LineWrap;  
   boolean JobRenderedAtHost;  
};  
```  
  
#### Parameters  
 **JobTermination**  
 Data Type: **sint16** Access Type: Read/Write  
  
 'EndBracket' means the job completes when the print server receives the End Bracket notification—otherwise, the print server spools the job until the session ends. The following table describes the possible values for **JobTermination**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|EndBracket|  
|1|UnBind|  
  
 **JobTimeoutSecs**  
 Data Type: **sint16** Qualifiers: **MINVALUE(0),MAXVALUE(99),UNITS("sec")** Access Type: Read/Write  
  
 The timeout for terminating 3270 print jobs—use with 'JobTimeout'.  
  
 **JobTimeout**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate whether a time-out will be used; otherwise, **false**. **JobTimeout** is most often used with **JobTimeoutSecs**.  
  
 **UseGDI**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that the Windows Graphical Device Interface (GDI) is used to format the print job; otherwise, **false**.  
  
 **TRNisASCII**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that transparent data from the host is in ASCII and needs no translation from EBCDIC to ASCII; otherwise, **false**.  
  
 **CustomTRN**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that a custom transparency byte, such as one other than the IBM standard of 0x35, will be used; otherwise, **false**.  
  
 **CustomTRNChar**  
 Data Type: **sint32** Qualifiers: <strong>MINVALUE(0),MAXVALUE(255)</strong>Access Type: Read/Write  
  
 The custom transparency byte—use this with 'CustomTRN' set to **true**.  
  
 **LUName**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE**Access Type: Read/Write  
  
 The 3270 printer LU for the print session.  
  
 **MonitorJob**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to cause the print server to send a message to the host stating that the print job completed; otherwise, **false**.  
  
 **LineWrap**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to line wrap; otherwise, **false**.  
  
 **JobRenderedAtHost**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that the print job is rendered at the host rather than by the Host Integration Server Host Print service; otherwise, **false**.  
  
## Remarks  
 **MsSna_PrintSession3270** uses 3270 protocols to communicate with the host.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)