---
title: "ExtractNextParameter2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f07d7d-c197-42ca-b280-4390b4077fd8
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# ExtractNextParameter
The **ExtractNextParameter** function is used to get the next parameter from a buffer. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          BOOL ExtractNextParameter(   
LPSTRszSourceBuffer,  
LPSTRszParameter,  
LPDWORDdStartIndex);  
```  
  
#### Parameters  
 *szSourceBuffer*  
 This supplied parameter specifies the source buffer.  
  
 *szParameter*  
 This supplied and returned parameter specifies the return buffer for parameters.  
  
 *dStartIndex*  
 This supplied parameter contains the DWORD index to begin parameter scan.  
  
## Return Value  
 TRUE  
 The function executed successfully and the next parameter was located and returned in the *szParameter* argument.  
  
 FALSE  
 The function failed.  
  
## Remarks  
 Parameters are delimited by a space character. Quotes can be used to include spaces in a parameter.