---
title: "APPC Definition1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: acc544db-b647-438e-99e9-04551ada16e7
caps.latest.revision: 3
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