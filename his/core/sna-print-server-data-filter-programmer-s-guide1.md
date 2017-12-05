---
title: "SNA Print Server Data Filter Programmer&#39;s Guide1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4dddb61e-c82f-4a92-90fb-fbc18155c136
caps.latest.revision: 4
---
# SNA Print Server Data Filter Programmer&#39;s Guide
The Host Print service of Microsoft® Host Integration Server 2010 provides server-based 3270 and 5250 printer emulation, enabling host applications to print to Local Area Network (LAN) printers supported by Microsoft Windows operating systems. This section introduces the SNA Print Server Data Filter API (sometimes referred to as the Print Exit API).  This API can be used to extend the capabilities of the Host Print service in Host Integration Server 2010.  
  
 The user can provide a print data filter DLL that will be called by Host Print service when a print job is initiated, when data is sent to the printer, and when the print job is completed. This print data filter DLL can:  
  
-   Send data to the printer when a job starts (print a banner page, for example).  
  
-   Perform special processing on the data to be printed.  
  
-   Send data to the printer upon print job completion (print a trailer page, for example).