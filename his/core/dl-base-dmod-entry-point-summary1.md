---
title: "DL-BASE-DMOD Entry Point Summary1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0a24f70-1c01-44c6-af00-cd7303e7378c
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# DL-BASE/DMOD Entry Point Summary
The following table shows entry points divided into the categories DL-BASE, Dynamic Access Module (DMOD), and buffer management, and listed in alphabetical order within each category.  
  
### DL-BASE entry points  
  
|DL-BASE entry points|Description|  
|---------------------------|-----------------|  
|[sbpuinit](../HIS2010/sbpuinit2.md)|Initializes the DL-BASE.|  
|[sbpurcvx](../HIS2010/sbpurcvx2.md)|Processes Open from routing procedure.|  
|[sbpusend](../HIS2010/sbpusend2.md)|Sends message.|  
|[sbputerm](../HIS2010/sbputerm2.md)|Terminates.|  
  
### DMOD entry points  
  
|DMOD entry points|Description|  
|-----------------------|-----------------|  
|[routproc](../HIS2010/routproc1.md)|Sample routing procedure.|  
|[sepdchnk](../HIS2010/sepdchnk1.md)|Gets the function management interface (FMI) chunk size.|  
|[sepdcrec](../HIS2010/sepdcrec2.md)|Gets user and diagnostics records from configuration file.|  
|[sepdgetinfo](../HIS2010/sepdgetinfo1.md)|Gets SNA server system information.|  
|[sepdrout](../HIS2010/sepdrout1.md)|Sets up the routing procedure (Microsoft® Windows® Server only).|  
  
### Buffer management entry points  
  
|Buffer management entry points|Description|  
|------------------------------------|-----------------|  
|[sbpibegt](../HIS2010/sbpibegt1.md)|Gets the buffer element.|  
|[sbpiberl](../HIS2010/sbpiberl1.md)|Releases the buffer element.|  
|[sepdbubl](../HIS2010/sepdbubl2.md)|Gets the buffer.|  
|[sepdburl](../HIS2010/sepdburl1.md)|Releases the buffer.|  
  
> [!NOTE]
>  The standard-call convention (CDECL) is used on Windows Server.  
  
> [!NOTE]
>  The format of buffer headers and elements is described in Messages. The formats of individual messages contained in buffers are defined in FMI Message Formats.