---
title: "SNA Print Server Data Filter Programmer&#39;s Reference2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68f6a705-b6c5-4329-9c05-cbf2a3dff68d
caps.latest.revision: 5
---
# SNA Print Server Data Filter Programmer&#39;s Reference
The Host Print Service feature of Host Integration Server 2010 provides server-based 3270 and 5250 printer emulation, enabling host applications to print to a Local Area Network (LAN) printer supported by Windows operating systems. This section introduces the SNA Print Server Data Filter API (sometimes referred to as the Print Exit API) that can be used to extend the capabilities of the Host Print Service in Host Integration Server.  
  
 This print data filter DLL can do the following:  
  
-   Send data to the printer when a job starts (print a banner page, for example).  
  
-   Perform special processing on the data to be printed.  
  
-   Send data to the printer upon print job completion (print a trailer page, for example).  
  
## In This Section  
 [SNA Print Server Data Filter API](../core/sna-print-server-data-filter-api2.md)  
  
 [PrtFilterAlloc](../core/prtfilteralloc1.md)  
  
 [PrtFilterFree](../core/prtfilterfree2.md)  
  
 [PrtFilterJobData](../core/prtfilterjobdata1.md)  
  
 [PrtFilterJobEnd](../core/prtfilterjobend2.md)  
  
 [PrtFilterJobStart](../core/prtfilterjobstart2.md)