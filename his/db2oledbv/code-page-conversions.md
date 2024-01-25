---
description: "Learn more about: Code Page Conversions"
title: "Code Page Conversions"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Code Page Conversions
The Data Provider supports a combination of single byte character sets (SBCS), mixed-byte character sets (MBCS) double-byte character sets (DBCS), and Unicode - UTF8 [1208], which is an 8-bit Unicode transformation format.  
  
## Host CCSID  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM DB2 database servers for z/OS and IBM i utilize EBCDIC (Extended Binary Coded Decimal Interchange Code).  
  
## PC Code Page  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode  
  
## Process Binary as Character  
 The optional Process binary (CCSID 65535) as character instructs the Data Provider to convert DB2 bytes to and from Windows character strings, based on an optional Binary Code Page property that is configured in the Data Source Wizard All Properties dialog. The default is false.  
  
## Binary Code Page  
 The Data Provider requires a binary code page number when supporting process binary as character. By default, this value is set to 0 (no code page conversion). Specify a positive four-digit numeric value for the Host CCSID, which corresponds to a coded character code set identifier (CCSID) supported by SNA National Language Support (SNANLS) in Host Integration Server.  
  
 For more information on code page conversion, see [SNA Internationalization Programmer's Reference](../core/sna-internationalization-programmer-s-guide1.md).
