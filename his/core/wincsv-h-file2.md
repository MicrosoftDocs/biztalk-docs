---
title: "WINCSV.H File2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52519262-62a2-4c72-a530-6190faaf43a8
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# WINCSV.H File
Use the **#include** command to include the WINCSV.H file in any application that issues CSVs.  
  
 The WINCSV.H file, which is included with the Microsoft® Host Integration Server Software Development Kit (SDK), contains:  
  
- The CSV function prototype.  
  
- The structure declarations for the CSV verb control blocks (VCBs).  
  
- The **#define** statements that substitute meaningful symbolic constants for hexadecimal values supplied to and returned by CSVs.  
  
  If a **#define** statement pertains to a hexadecimal value that is longer than one byte, a comment shows how the hexadecimal value is stored in memory.  
  
  When setting or testing CSV parameters, use the symbolic constants defined by the WINCSV.H file. When examining trace files or the contents of memory, use the hexadecimal values.