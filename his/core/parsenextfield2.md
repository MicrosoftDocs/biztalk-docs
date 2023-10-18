---
description: "Learn more about: ParseNextField"
title: "ParseNextField2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ParseNextField
The **ParseNextField** function is used to parse and return the next field from string. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
        void ParseNextField(  
        LPSTR  
        szParseString,  
LPSTRszField,  
charscDelimiter,  
LPDWORDdStartIndex);  
```  
  
#### Parameters  
 *szParseString*  
 This supplied parameter specifies the string to parse.  
  
 *szField*  
 This supplied and returned specifies the return buffer for the next field.  
  
 *scDelimiter*  
 This supplied parameter specifies the delimiter character for the end of a field.  
  
 *dStartIndex*  
 This supplied parameter specifies a pointer to the index in bytes from beginning of the *szParseString* to start the search from.  
  
## Return Value  
 TRUE  
 The next field was found.  
  
 FALSE  
 The next field was not found.  
  
> [!NOTE]
>  The **'^'** character can be used as an escape character to allow the delimiter to be used.
