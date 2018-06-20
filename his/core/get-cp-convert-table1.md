---
title: "GET_CP_CONVERT_TABLE1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a35420f-19d7-4763-a020-5166084f1bda
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# GET_CP_CONVERT_TABLE
The **GET_CP_CONVERT_TABLE** verb creates and returns a 256-byte conversion table to translate character strings from a source code page to a target code page.  
  
 The following structure describes the verb control block (VCB) used by the **GET_CP_CONVERT_TABLE** verb.  
  
## Syntax  
  
```  
  
struct get_cp_convert_table {  
    unsigned short       opcode;  
    unsigned char        opext;  
    unsigned char        reserv2;  
    unsigned short       primary_rc;  
    unsigned long        secondary_rc;  
    unsigned char        reserv3[8];  
    unsigned short       source_cp;  
    unsigned short       target_cp;  
    unsigned char FAR *  conv_tbl_addr;  
    unsigned char        char_not_fnd;  
    unsigned char        substitute_char;  
};  
```  
  
## Remarks  
  
## Members  
 *opcode*  
 Supplied parameter. The verb identifying the operation code, SV_GET_CP_CONVERT_TABLE.  
  
 *opext*  
 A reserved field.  
  
 *reserv2*  
 A reserved field.  
  
 *primary_rc*  
 Returned parameter. Specifies the primary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *secondary_rc*  
 Returned parameter. Specifies the secondary return code set by APPC at the completion of the verb. The valid return codes vary depending on the APPC verb issued. See Return Codes for valid error codes for this verb.  
  
 *reserv3*  
 A reserved field.  
  
 *source_cp*  
 Supplied parameter. Specifies the source code page from which characters are converted. The allowed code pages (decimal values) are as follows:  
  
- ASCII 437, 850, 860, 863, 865  
  
- EBCDIC 037, 273, 277, 278, 280, 284, 285, 297, 500  
  
  User-defined code pages in the range from 65280 through 65535 are also allowed.  
  
  ASCII code pages are sometimes referred to as PC code pages; EBCDIC code pages are sometimes referred to as host code pages.  
  
  *target_cp*  
  Supplied parameter. Specifies the target code page to which characters are converted. For allowed code pages, see the preceding definition for **source_cp**.  
  
  *conv_tbl_addr*  
  Supplied parameter. Specifies the address of the buffer to contain the 256-byte conversion table. The buffer must be in a writable segment and long enough to contain the table.  
  
  *char_not_fnd*  
  Supplied parameter. Specifies the action to take if a character in the source code page does not exist in the target code page:  
  
- Use SV_ROUND_TRIP to store a unique value in the conversion table for each source code page character.  
  
- Use SV_SUBSTITUTE to store a substitute character (specified by **substitute_char**) in the conversion table.  
  
  *substitute_char*  
  Supplied parameter. Specifies the character to store in the conversion table when a character from the source code page has no equivalent in the target code page.  
  
## Return Codes  
 SV_OK  
 Primary return code; the verb executed successfully.  
  
 SV_PARAMETER_CHECK  
 Primary return code; the verb did not execute because of a parameter error.  
  
 SV_INVALID_CHAR_NOT_FOUND  
  
 Secondary return code; the **char_not_fnd** parameter contained an invalid value.  
  
 SV_INVALID_DATA_SEGMENT  
  
 Secondary return code; the 256-byte area specified for the conversion table extended beyond the segment boundary, or the segment was not writable.  
  
 SV_INVALID_SOURCE_CODE_PAGE  
  
 Secondary return code; the code page specified by **source_cp** is not supported.  
  
 SV_INVALID_TARGET_CODE_PAGE  
  
 Secondary return code; the code page specified by **target_cp** is not supported.  
  
 SV_COMM_SUBSYSTEM_NOT_LOADED  
 Primary return code; a required component could not be loaded or terminated while processing the verb. Thus, communication could not take place. Contact the system administrator for corrective action.  
  
 SV_INVALID_VERB  
 Primary return code; the **opcode** parameter did not match the operation code of any verb. No verb executed.  
  
 SV_INVALID_VERB_SEGMENT  
 Primary return code; the VCB extended beyond the end of the data segment.  
  
 SV_UNEXPECTED_DOS_ERROR  
 Primary return code; one of the following conditions occurred:  
  
-   The Microsoft® Windows® system encountered an error while processing the verb. The operating system return code was returned through the secondary return code. If the problem persists, contact the system administrator for corrective action.  
  
-   A CSV was issued from a message loop that was invoked by another application issuing a Windows **SendMessage** function call, rather than the more common Windows **PostMessage** function call. Verb processing cannot take place.  
  
-   A CSV was issued when **SendMessage** invoked your application. You can determine whether your application has been invoked with **SendMessage** by using the **InSendMessage** Windows API function call.  
  
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
  
  The first character of the source string can be any character in the character set except the space.  
  
  During conversion, embedded blanks (including blanks in the first position) are converted to 0x00. Although such a conversion will complete, CONVERSION_ERROR is returned as the secondary return code, indicating that the CSV library has completed an irreversible conversion on the supplied data.  
  
  For Windows, a description of COMTBLG should point to the Windows registry under **\SnaBase\Parameters\Client**. For the OS/2 operating system, the directory and file containing the table must be specified by the environment variable COMTBLG. (If the file is not found, the system returns the SV_TABLE_ERROR parameter check.).  
  
  The SV_ROUND_TRIP value for **char_not_fnd** is useful only if you build a second conversion table to convert between the same two code pages in the reverse direction. If you specify the SV_ROUND_TRIP value in building both conversion tables, any character translated from one code page to the other and then back will be unchanged.  
  
  When using the SV_SUBSTITUTE value for **char_not_fnd**, converting the translated character string back to the original code page will not necessarily re-create the original character string.  
  
  Use **substitute_char** only if **char_not_fnd** is set to SV_SUBSTITUTE.  
  
  The value stored in the conversion table is the ASCII value associated with the character. If the table is used for conversion from ASCII to EBCDIC, the character that appears in the converted string is the character associated with the numeric EBCDIC value rather than ASCII.  
  
  For example, if you supply the underscore (*) character (ASCII value F6) while creating an ASCII to EBCDIC conversion table, the character that appears in the converted strings will be 6, the character associated with the value F6 in EBCDIC. To use the \\* character as the substitute character in an ASCII to EBCDIC conversion table, you should supply the value E1 (the value associated with the \_ character in EBCDIC) rather than the actual character.  
  
  A code page is a table that associates specific ASCII or EBCDIC values with specific characters. If a character from the source code page does not exist in the target code page, the translated (target) string differs from the original (source) string.