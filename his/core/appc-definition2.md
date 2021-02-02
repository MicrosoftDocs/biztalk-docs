---
description: "Learn more about: APPC Definition"
title: "APPC Definition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 855405a1-6801-4ff3-9fd9-b8730147343a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
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
