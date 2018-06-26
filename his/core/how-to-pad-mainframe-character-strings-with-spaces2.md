---
title: "How to Pad Mainframe Character Strings with Spaces2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7c398ad-cdb5-486d-a08c-fc163533aa80
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Pad Mainframe Character Strings with Spaces
You can define the properties for a string such that the Transaction Integrator (TI) run-time environment adds space characters to pad the mainframe representation of the string instead of depending on a null termination character.  
  
### To use either a space character or null termination character  
  
1. In Microsoft Visual Studio, right-click the object, and then click **Properties**.  
  
2. Under **Host Data Type Information** in the **Properties** pane, click **String Delimiting**.  
  
3. Select either **Space Padded** or **Null Terminated**.  
  
   The following table describes what happens with each delimiting option (**Space Padded** or **Null terminated**) when converting to the type of string indicated.  
  
|Type of string operation|What happens for each type of string delimiting operation|  
|------------------------------|---------------------------------------------------------------|  
|Conversion to EBCDIC string|**Space Padded.** The TI run-time environment adds single-byte space characters to the end of the string until all bytes in the PIC X formatted string are filled.|  
||**Null terminated.** The TI run-time environment adds a single null character to the end of the string if there is room in the PIC X count for the byte.|  
|Conversion from EBCDIC string|**Space Padded.** The TI run-time environment strips single-byte space characters from the end of the string.|  
||**Null terminated.** The TI run-time environment scans from the beginning of the string and stops the conversion at the first null character it encounters in the string.|  
|Conversion to DBCS string|**Space Padded.** The TI run-time environment adds double-byte space characters to the end of the string until all characters in the PIC G formatted string are filled.|  
||**Null terminated.** The TI run-time environment adds a double-byte character set (DBCS) null character to the end of the string if there is room in the PIC G count for the bytes.|  
|Conversion from DBCS string|**Space Padded.** The TI run-time environment strips double-byte space characters from the end of the string.|  
||**Null terminated.** The TI run-time environment scans from the beginning of the string and stops the conversion at the first DBCS null character it encounters in the string.|  
|Conversion to Intermixed string|**Space Padded.** The TI run-time environment adds single-byte space characters to the end of the string until all bytes in the PIC X formatted string are filled. If the terminating character in the UNICODE string maps to a DBCS character, the TI run-time environment adds an SI character before it adds the space characters.|  
||**Null terminated.** The TI run-time environment adds a single byte null character to the end of the string if there is room in the PIC X count. If the terminating character in the UNICODE string maps to a DBCS character, the TI run-time environment adds an SI character before it adds the null character.|  
|Conversion from Intermixed string|**Space Padded.** The TI run-time environment strips the terminating single-byte and double-byte space characters from the end of the string. When it strips the space characters, the TI run-time environment treats any terminating SI character as if it were a space.|  
||**Null terminated.** The TI run-time environment scans from the beginning of the string and stops the conversion at the first null character (of either width) it encounters.|  
  
 Special handling occurs for a string that is last in the host buffer and that is flagged as *last is variable*. For example:  
  
- **Space Padded.** Upon conversion to an Extended Binary Coded Decimal Interchange Code (EBCDIC) string, the string is terminated by the length count of the containing buffer, so it contains no additional space characters. Upon conversion from an EBCDIC string, the buffer is considered terminated by the length count of the containing buffer; then the string is examined for blank padding. The host can send this string blank padded beyond the significant data or not blank padded but with the last significant character of the string in the last position in the containing buffer. The space character is determined by the type of string (single, double, or intermixed).  
  
- **Null terminated.** Upon conversion to an EBCDIC string, the string is sent as is. The TI run-time environment checks the length of the string, and then checks that the exact number of characters is sent. In other words, the number of characters sent is equal to the length of the string. No null terminator or spaces are appended to the end of the string.  
  
  The following tables show how string delimiting works when the **String delimiting** property is set to **Space Padded** versus **Null terminated** in combination with the variable size setting. All examples assume the mainframe data declaration as PIC X(5). "b" represents a space,"?" represents unassigned data, and "\0" represents a null.  
  
### String delimiting set to Space Padded and variable size not active  
  
|Workstation|Direction|Mainframe|  
|-----------------|---------------|---------------|  
|ABC\0|To Host|'ABCbb'|  
|ABCb|To Host|'ABCbb'|  
|CBA|From Host|'CBAbb'|  
|CBA\0?|From Host|'CBA\0?'|  
|CBA\0|From Host|'CBA\0b'|  
  
### String delimiting set to Space Padded and variable size active  
  
|Workstation|Direction|Mainframe|  
|-----------------|---------------|---------------|  
|ABC\0|To Host|'ABC'|  
|Abb|To Host|'Abb'|  
|CBA|From Host|'CBAbb'|  
|CBA\0?|From Host|'CBA\0?'|  
|CBA\0|From Host|'CBA\0b'|  
  
### String delimiting set to Null terminated and variable size not active  
  
|Workstation|Direction|Mainframe|  
|-----------------|---------------|---------------|  
|ABC\0|To Host|'ABC\0?'|  
|ABC|From Host|'ABC\0?'|  
|ABCbb|From Host|'ABCbb'|  
|ABC|From Host|ABC\0\0'|  
  
### String delimiting set to Null terminated and variable size active  
  
|Workstation|Direction|Mainframe|  
|-----------------|---------------|---------------|  
|ABC\0|To Host|'ABC\0'|  
|ABC|From Host|'ABC\0?'|  
|ABCbb|From Host|'ABCbb'|  
|ABC|From Host|ABC\0\0'|  
  
## See Also  
 [Mainframe Character Strings and Code Pages](../core/mainframe-character-strings-and-code-pages2.md)