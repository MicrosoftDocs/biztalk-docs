---
description: "Learn more about: SnaNlsMapString"
title: "SnaNlsMapString1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SnaNlsMapString
The **SnaNlsMapString** function is called to translate a string from one code page to another.  
  
## Syntax  
  
```  
  
int WINAPI SnaNlsMapString(   
LPCTSTR lpSrcStr,  
LPTSTR lpDestStr,  
UINT inCodePage,  
UINT outCodePage,  
Int in_length,  
int out_length,  
UINT in_type,  
UINT out_type,  
WORD *Options,  
LONG*lConvRequiredLen  
);  
```  
  
#### Parameters  
 *lpSrcStr*  
 Supplied parameter. The input source string to be translated.  
  
 *lpDestStr*  
 Returned parameter. The translated string which may be NULL if *out_length* was zero.  
  
 *inCodePage*  
 Supplied parameter. Specifies the code page of the incoming source string; ignored if the input is Unicode.  
  
 *outCodePage*  
 Supplied parameter. Specifies the code page of the output translated string; ignored if the output is Unicode.  
  
 *in_length*  
 Supplied parameter. Specifies the length of the input source string in characters if the input is multibyte or in wide characters if the input is Unicode.  
  
 *out_length*  
 Supplied parameter. Specifies the maximum length available for the output translated string in characters if the output is multibyte or in wide characters if the output is Unicode.  
  
 *in_type*  
 Supplied parameter. Specifies the type of the input source string. Possible values for *in_type* are SNA_MULTIBYTE for multibyte and SNA_UNICODE for Unicode.  
  
 *out_type*  
 Supplied parameter. Specifies the type of the output translated string. Possible values for *out_type* are SNA_MULTIBYTE for multibyte and SNA_UNICODE for Unicode.  
  
 *Options*  
 Supplied and returned parameter. As a supplied parameter, this specifies a set of options that may be applied to the translation process, including TrnsDT options and the default character for the translation. On return, this parameter indicates the required buffer length for the output translated string if the function call failed.  
  
 *lConvRequiredLen*  
 Returned parameter. Required buffer length if call failed.  
  
## Return Value  
 The **SnaNlsMapString** function returns the number of characters or wide characters written to *lpDestStr* on success; otherwise 0 is returned on failure.  
  
 On failure, the Win32® **GetLastError** function should be used to return an error code indicating the cause of the failure. Possible values returned by GetLastError are as follows:  
  
 ERROR_NOT_SUPPORTED  
  
 This error is returned for two possible reasons—either the NLS language resource file is not available or the *in_type* and *out_type* of the source and destination strings are not of the same type.  
  
 ERROR_BUFFER_OVERFLOW  
  
 This error is returned if the output buffer is too small. In such cases, the *Options* parameter returns with the value needed for *out_length*.  
  
 ERROR_INVALID_PARAMETER  
  
 This error is returned if a bad value was passed in a parameter; for example, if the *in_type* or *out_type* parameters contained undefined values.  
  
 ERROR_INVALID_DATA  
  
 This error is returned if a bad value was passed in the *lpSrcStr* parameter; for example, if the input string has a lead byte at the end.  
  
 ERROR_OUTOFMEMORY  
  
 This error is returned if memory could not be allocated for use by the SNANLS DLL.
