---
description: "Learn more about: Supported COBOL Data Types"
title: "Supported COBOL Data Types2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28a4da9e-4461-407b-8595-b8bdf33dfa42
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Supported COBOL Data Types
**COMP-1**  
 A 4-byte, single precision, floating-point Real data type that specifies internal floating-point items. The sign is contained in the first bit of the leftmost byte, and the exponent is contained in the remaining seven bits of that byte. The remaining three bytes hold the mantissa.  
  
 **COMP-2**  
 An 8-byte, double precision, floating-point Real data type that specifies internal floating-point items. The sign is contained in the first bit of the leftmost byte, and the exponent is contained in the remaining seven bits of the first byte. The remaining seven bytes hold the mantissa.  
  
 **COMP-3 Packed Decimal**  
 A packed decimal data type that specifies internal decimal items stored in packed decimal format. In the packed decimal format, each byte in a field represents two numeric digits except for the rightmost byte. The rightmost byte holds one digit and the sign. In other words, there are two digits in each character position except for the trailing character position that is occupied by the low-order digit and sign. The item can contain any of the digits from 0 through 9, plus a sign, to represent a value not exceeding 18 decimal digits. For example, the decimal value +123 is represented in two bytes as 0001 0010 0011 1100 in packed decimal format. For more information see, [Zoned Decimal or Packed Decimal Data Types](../core/zoned-decimal-or-packed-decimal-data-types1.md).  
  
 **DISPLAY Zoned Decimal**  
 An unpacked decimal data type that specifies internal decimal items stored in zoned decimal format. Zoned decimal format is synonymous with unpacked decimal format, which is a format for representing numbers where each digit is contained in bits 4 through 7 and the sign is contained in bits 0 through 3 of the least significant byte. Bits 0 through 3 of all bytes other than the least significant byte contain 1s (hex F). For example, the decimal value +123 is represented in three bytes as 1111 0001 1111 0010 1100 0011 in zoned decimal format. For more information see, [Zoned Decimal or Packed Decimal Data Types](../core/zoned-decimal-or-packed-decimal-data-types1.md).  
  
 **DATE and TIME**  
 Specifies a date and time by using group item of two PIC 9(7) COMP-3 Packed Decimal value.  
  
 **TIME only**  
 Specifies a time by using a PIC 9(7) COMP-3 Packed Decimal value.  
  
 **DATE only**  
 Specifies a date by using a PIC 9(7) COMP-3 Packed Decimal value.  
  
 **PIC X**  
 Specifies a single character in an Extended Binary Coded Decimal Interchange Code (EBCDIC) character string. EBCDIC is the native representation for character data on mainframes and AS/400s. Unicode is the native representation for character data on Windows-based platforms.  
  
 **PIC X No Translation**  
 Specifies a single COBOL character in an EBCDIC character string that is handled as if it were binary data. In other words, there is no translation from EBCDIC to Unicode or from Unicode to EBCDIC.  
  
 **PIC G**  
 Specifies a double-byte EBCDIC string.  
  
 **PIC S9(4) COMP (Integer 16-bit)**  
 Specifies an integer that is 16 bits, or 2 bytes, in length.  
  
 **PIC S9(9) COMP (Integer 32-bit)**  
 Specifies an integer that is 32 bits, or 4 bytes, in length.  
  
## See Also  
 [Supported TI Data Types](../core/supported-ti-data-types2.md)
