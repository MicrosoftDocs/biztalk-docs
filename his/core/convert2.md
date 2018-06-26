---
title: "CONVERT2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c2fdae6-e52d-412a-944b-3949b38cf25e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# CONVERT
The **CONVERT** verb translates an ASCII character string to EBCDIC or an EBCDIC character string to ASCII. The string to be converted is called the source string. The converted string is called the target string.  
  
 The following structure describes the verb control block (VCB) used by the **CONVERT** verb.  
  
## Syntax  
  
```  
  
struct convert {  
    unsigned short       opcode;  
    unsigned char        opext;  
    unsigned char        reserv2;  
    unsigned short       primary_rc;  
    unsigned long        secondary_rc;  
    unsigned char        direction;  
    unsigned char        char_set;  
    unsigned short       len;  
    unsigned char FAR *  source;  
    unsigned char FAR *  target;  
};  
```  
  
## Members  
 *opcode*  
 Supplied parameter. The verb identifying the operation code, SV_CONVERT.  
  
 *opext*  
 A reserved field.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *direction*  
 Supplied parameter. Specifies the direction of the conversion. To convert from ASCII to EBCDIC, use SV_ASCII_TO_EBCDIC. To convert from EBCDIC to ASCII, use SV_EBCDIC_TO_ASCII.  
  
 *char_set*  
 Supplied parameter. Specifies the character set to use in converting the source string. Allowed values include SV_A (type A character set), SV_AE (type AE character set), and SV_G (user-defined type G character set).  
  
 *len*  
 Supplied parameter. Specifies the number of characters to be converted.  
  
 This length plus the offset from the beginning of the source or target buffer must not exceed the segment boundary.  
  
 *source*  
 Supplied parameter. Specifies the address of the buffer containing the character string to be converted.  
  
 *target*  
 Supplied parameter. Specifies the address of the buffer to contain the converted character string.  
  
 This buffer can overlap or coincide with the buffer pointed to by the **source** parameter. In this case, the converted data string overwrites the source data string.  
  
## Return Codes  
 SV_OK  
 Primary return code; the verb executed successfully.  
  
 SV_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 SV_CONVERSION_ERROR  
  
 Secondary return code; one or more characters in the source string were not found in the conversion table. These characters were converted to nulls (0x00). The verb still executed.  
  
 SV_INVALID_CHARACTER_SET  
  
 Secondary return code; the **char_set** parameter contained an invalid value.  
  
 SV_INVALID_DATA_SEGMENT  
  
 Secondary return code; the data buffer containing the source or target string did not fit in one segment, or the target segment was not a read/write segment.  
  
 SV_INVALID_DIRECTION  
  
 Secondary return code; the direction contained an invalid value.  
  
 SV_INVALID_FIRST_CHARACTER  
  
 Secondary return code; the first character of a type A source string was invalid.  
  
 SV_TABLE_ERROR  
  
 Secondary return code; one of the following occurred:  
  
- The file containing the user-written type G conversion table was not specified by the environment variable CSVTBLG.  
  
- The table was not in the correct format.  
  
- The file specified by the CSVTBLG variable was not found.  
  
  SV_COMM_SUBSYSTEM_NOT_LOADED  
  Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
  SV_INVALID_VERB  
  Primary return code; the **opcode** parameter did not match the operation code of any verb. No verb executed.  
  
  SV_INVALID_VERB_SEGMENT  
  Primary return code; the VCB extended beyond the end of the data segment.  
  
  SV_UNEXPECTED_DOS_ERROR  
  Primary return code; one of the following conditions occurred:  
  
- The Microsoft Windows system encountered an error while processing the verb. The operating system return code was returned through the secondary return code. If the problem persists, contact the system administrator for corrective action.  
  
- A CSV was issued from a message loop that was invoked by another application issuing a Windows **SendMessage** function call, rather than the more common Windows **PostMessage** function call. Verb processing cannot take place.  
  
- A CSV was issued when **SendMessage** invoked your application. You can determine whether your application has been invoked with **SendMessage** by using the **InSendMessage** Windows API function call.  
  
## Remarks  
 The type A character set consists of:  
  
- Uppercase letters.  
  
- Numerals 0 through 9.  
  
- Special characters $, #, @, and space.  
  
  This character set is supported by a system-supplied type A conversion table.  
  
  The first character of the source string must be an uppercase letter or the special character $, #, or @. Spaces are allowed only in trailing positions. Lowercase ASCII letters are translated to uppercase EBCDIC letters when the direction is ASCII to EBCDIC.  
  
  The type AE character set consists of:  
  
- Uppercase letters.  
  
- Lowercase letters.  
  
- Numerals 0 through 9.  
  
- Special characters $, #, @, period, and space.  
  
  This character set is supported by a system-supplied type AE conversion table.  
  
  The first character of the source string can be any character in the character set, except the space. Spaces are allowed only in trailing positions.  
  
  During conversion, embedded blanks (including blanks in the first position) are converted to 0x00. Although such a conversion will complete, CONVERSION_ERROR is returned as the secondary return code, indicating that the CSV library has completed an irreversible conversion on the supplied data.  
  
  For Windows a description of COMTBLG should point to the Windows registry under **\SnaBase\Parameters\Client**.  
  
  The data for a type G conversion table must be an ASCII file 32 lines long. Each line must consist of 32 hexadecimal digits, representing 16 characters, and be terminated by a carriage return and line feed. The first 16 lines (256 characters) specify the EBCDIC characters to which ASCII characters are converted; the remaining 16 lines specify the ASCII characters to which EBCDIC characters are converted.  
  
  The hexadecimal digits A through F can be either uppercase or lowercase. However, you may want to make these digits uppercase to ensure compatibility with IBM ES for OS/2 version 1.0.  
  
> [!NOTE]
>  You can use [GET_CP_CONVERT_TABLE](../core/get-cp-convert-table1.md) to build a type G user-written conversion table in memory, and then store the table in a file.