---
title: "SNA Sense Codes2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f1ae79d-4c11-4b9d-ab61-aaab843a9569
caps.latest.revision: 4
---
# SNA Sense Codes
If there is a communication problem during an SNA session, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] can generate sense codes that notify the remote system of the type of problem. The sense codes fall into five distinct categories, corresponding to the type of problem that occurred.  
  
|Value|Category|  
|-----------|--------------|  
|X'08'|Request Reject|  
|X'10'|Request Error|  
|X'20'|State Error|  
|X'40'|RH Usage Error|  
|X'80'|Path Error|  
  
 The following sections list the sense codes by category, and include two additional categories of sense codes:  
  
-   Sense codes sent by a 3270 emulator on LUSTAT requests  
  
-   Sense codes that can only flow on LU 6.2 sessions  
  
## In This Section  
 [Request Reject (Category X'08')](../HIS2010/request-reject-category-x-08-2.md)  
  
 [Request Errors (Category X'10')](../HIS2010/request-errors-category-x-10-1.md)  
  
 [State Errors (Category X'20')](../HIS2010/state-errors-category-x-20-2.md)  
  
 [RH Usage Errors (Category X'40')](../HIS2010/rh-usage-errors-category-x-40-2.md)  
  
 [Path Errors (Category X'80')](../HIS2010/path-errors-category-x-80-1.md)  
  
 [LUSTAT Sense Codes](../HIS2010/lustat-sense-codes2.md)  
  
 [Sense Data Specific to LU 6.2](../HIS2010/sense-data-specific-to-lu-6-22.md)