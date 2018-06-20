---
title: "CPI-C Calls in C Programs (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0ae3220c-7377-4660-91ba-0db84113e1d4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# CPI-C Calls in C Programs (CPI-C)
This implementation of Common Programming Interface for Communications (CPI-C) is available to programs written in Microsoft® C version 6 or later.  
  
 The WINCPIC.H header file defines the prototypes for each CPI-C function. Other definitions include:  
  
- Types specifically defined for use by CPI-C parameters.  
  
- The structure of the side information entries.  
  
- Symbolic names defined for integer parameters.  
  
  To use CPI-C calls, the C program must include WINCPIC.H and declare the variables to be used in passing parameters on CPI-C calls.  
  
  Note that you must define WIN32® before including WINCPIC.H  
  
  For example:  
  
```  
#define WIN32  
#include <wincpic.h>  
```  
  
 In the case of strings, the program must also determine the preferred string length.