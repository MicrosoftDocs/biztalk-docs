---
description: "Learn more about: SNA Print Server Data Filter Programmer&#39;s Guide"
title: "SNA Print Server Data Filter Programmer&#39;s Guide2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNA Print Server Data Filter Programmer&#39;s Guide
The Host Print service of Host Integration Server provides server-based 3270 and 5250 printer emulation, enabling host applications to print to Local Area Network (LAN) printers supported by Microsoft Windows operating systems. This section introduces the SNA Print Server Data Filter API (sometimes referred to as the Print Exit API).  This API can be used to extend the capabilities of the Host Print service in Host Integration Server.  
  
 The user can provide a print data filter DLL that will be called by Host Print service when a print job is initiated, when data is sent to the printer, and when the print job is completed. This print data filter DLL can:  
  
-   Send data to the printer when a job starts (print a banner page, for example).  
  
-   Perform special processing on the data to be printed.  
  
-   Send data to the printer upon print job completion (print a trailer page, for example).
