---
title: "DL-BASE-DMOD Entry Point Summary2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fed40da-109c-4a02-bc61-3d6bf7385279
caps.latest.revision: 4
---
# DL-BASE/DMOD Entry Point Summary
The following table shows entry points divided into the categories DL-BASE, Dynamic Access Module (DMOD), and buffer management, and listed in alphabetical order within each category.  
  
### DL-BASE entry points  
  
|DL-BASE entry points|Description|  
|---------------------------|-----------------|  
|[sbpuinit](../core/sbpuinit2.md)|Initializes the DL-BASE.|  
|[sbpurcvx](../core/sbpurcvx2.md)|Processes Open from routing procedure.|  
|[sbpusend](../core/sbpusend2.md)|Sends message.|  
|[sbputerm](../core/sbputerm2.md)|Terminates.|  
  
### DMOD entry points  
  
|DMOD entry points|Description|  
|-----------------------|-----------------|  
|[routproc](../core/routproc1.md)|Sample routing procedure.|  
|[sepdchnk](../core/sepdchnk1.md)|Gets the function management interface (FMI) chunk size.|  
|[sepdcrec](../core/sepdcrec2.md)|Gets user and diagnostics records from configuration file.|  
|[sepdgetinfo](../core/sepdgetinfo1.md)|Gets SNA server system information.|  
|[sepdrout](../core/sepdrout1.md)|Sets up the routing procedure (Microsoft® Windows® Server only).|  
  
### Buffer management entry points  
  
|Buffer management entry points|Description|  
|------------------------------------|-----------------|  
|[sbpibegt](../core/sbpibegt1.md)|Gets the buffer element.|  
|[sbpiberl](../core/sbpiberl1.md)|Releases the buffer element.|  
|[sepdbubl](../core/sepdbubl2.md)|Gets the buffer.|  
|[sepdburl](../core/sepdburl1.md)|Releases the buffer.|  
  
> [!NOTE]
>  The standard-call convention (CDECL) is used on Windows Server.  
  
> [!NOTE]
>  The format of buffer headers and elements is described in Messages. The formats of individual messages contained in buffers are defined in FMI Message Formats.