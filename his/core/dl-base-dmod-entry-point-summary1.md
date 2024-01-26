---
description: "Learn more about: DL-BASE/DMOD Entry Point Summary"
title: "DL-BASE-DMOD Entry Point Summary1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# DL-BASE/DMOD Entry Point Summary
The following table shows entry points divided into the categories DL-BASE, Dynamic Access Module (DMOD), and buffer management, and listed in alphabetical order within each category.  
  
### DL-BASE entry points  
  
|DL-BASE entry points|Description|  
|---------------------------|-----------------|  
|[sbpuinit](./sbpuinit1.md)|Initializes the DL-BASE.|  
|[sbpurcvx](./sbpurcvx1.md)|Processes Open from routing procedure.|  
|[sbpusend](./sbpusend1.md)|Sends message.|  
|[sbputerm](./sbputerm1.md)|Terminates.|  
  
### DMOD entry points  
  
|DMOD entry points|Description|  
|-----------------------|-----------------|  
|[routproc](./routproc2.md)|Sample routing procedure.|  
|[sepdchnk](./sepdchnk2.md)|Gets the function management interface (FMI) chunk size.|  
|[sepdcrec](./sepdcrec1.md)|Gets user and diagnostics records from configuration file.|  
|[sepdgetinfo](./sepdgetinfo2.md)|Gets SNA server system information.|  
|[sepdrout](./sepdrout2.md)|Sets up the routing procedure (Microsoft® Windows® Server only).|  
  
### Buffer management entry points  
  
|Buffer management entry points|Description|  
|------------------------------------|-----------------|  
|[sbpibegt](./sbpibegt2.md)|Gets the buffer element.|  
|[sbpiberl](./sbpiberl2.md)|Releases the buffer element.|  
|[sepdbubl](./sepdbubl1.md)|Gets the buffer.|  
|[sepdburl](./sepdburl2.md)|Releases the buffer.|  
  
> [!NOTE]
>  The standard-call convention (CDECL) is used on Windows Server.  
  
> [!NOTE]
>  The format of buffer headers and elements is described in Messages. The formats of individual messages contained in buffers are defined in FMI Message Formats.
