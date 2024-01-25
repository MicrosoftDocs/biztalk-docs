---
description: "Learn more about: APPC Definition"
title: "APPC Definition2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# APPC Definition
The prototype definitions of the **APPC** function are as follows:  
  
## Syntax  
  
```  
  
void WINAPI APPC(long);  
HANDLE WINAPI WinAsyncAPPC (hWnd, LPAPPC);  
```  
  
## Remarks  
 The verb control block (VCB) address parameter, a 32-bit pointer, is declared as a long integer and thus requires casting from a pointer to a long integer.
