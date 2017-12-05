---
title: "WINCSV Definition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28764e7c-221f-4151-a0d4-c34b6b996782
caps.latest.revision: 3
---
# WINCSV Definition
The prototype definition of the **WINCSV** function is as follows:  
  
```  
extern void WINAPI WINCSV (LPCSV);  
  
```  
  
 The verb control block (VCB) address parameter, a 32-bit pointer, is declared as a long integer and requires casting from a pointer to a long integer.