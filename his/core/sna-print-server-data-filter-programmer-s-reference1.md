---
title: "SNA Print Server Data Filter Programmer&#39;s Reference1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe26ec67-8ecd-4f52-850b-574d241148d5
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SNA Print Server Data Filter Programmer&#39;s Reference
The Host Print Service feature of Host Integration Server 2013 provides server-based 3270 and 5250 printer emulation, enabling host applications to print to a Local Area Network (LAN) printer supported by Windows operating systems. This section introduces the SNA Print Server Data Filter API (sometimes referred to as the Print Exit API) that can be used to extend the capabilities of the Host Print Service in Host Integration Server.  
  
 This print data filter DLL can do the following:  
  
-   Send data to the printer when a job starts (print a banner page, for example).  
  
-   Perform special processing on the data to be printed.  
  
-   Send data to the printer upon print job completion (print a trailer page, for example).  
  
## In This Section  
 [SNA Print Server Data Filter API](../core/sna-print-server-data-filter-api1.md)  
  
 [PrtFilterAlloc](../core/prtfilteralloc2.md)  
  
 [PrtFilterFree](../core/prtfilterfree1.md)  
  
 [PrtFilterJobData](../core/prtfilterjobdata2.md)  
  
 [PrtFilterJobEnd](../core/prtfilterjobend1.md)  
  
 [PrtFilterJobStart](../core/prtfilterjobstart1.md)