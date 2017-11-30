---
title: "SNA Performance Monitor Interface2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f1a9d7e-6468-4ef3-84fd-76d872d534ec
caps.latest.revision: 4
---
# SNA Performance Monitor Interface
This section describes the interface for performance monitoring (Perfmon) used by SNADIS links that Microsoft [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] supplies. This interface is provided to simplify the integration of SNADIS-compliant link services with the Microsoft Windows System Monitor applications. It provides a common look-and-feel to all link service performance counters exported by SNADIS links, independent of the vendor and link transport (channel, Twinax, SDLC, X.25, TR, E/Net, and so on).  
  
 The performance monitoring statistics maintained for an SNA link service are stored in a series of [ADAPTERCOUNTER](../HIS2010/adaptercounter1.md) structures that are members of an [ADAPTERPERFDATA](../HIS2010/adapterperfdata1.md) structure. These structures are defined in the SEMFPERF.H header file.  
  
 Three API entry points are exported from IHVLINK.DLL (and the IHVLINK.LIB import library) that are used by the Perfmon API. These functions should be called in the order noted below at link service initialization time.  
  
 To support performance monitoring, an SNA Link driver first calls [SNAInitLinkPerfmon](../HIS2010/snainitlinkperfmon2.md)to initialize data structures used by the Perfmon application. This call should be followed with a call to the function [SNAGetLinkPerfArea](../HIS2010/snagetlinkperfarea1.md), which returns a shared mutex handle and a pointer to the shared data area for the **ADAPTERPERFDATA** structure used by the Perfmon application to store the link statistics. This handle and shared memory data area parameter are the returned values from **SNAInitLinkPerfmon**. Finally, the [SNAGetPerfValues](../HIS2010/snagetperfvalues2.md) function is called to fill in the *ServiceNameIndex* and *FirstCounterIndex* fields so that the Perfmon application knows where to get the descriptions of the performance counters from the registry.  
  
 After these three calls have been made, the SNA link driver simply maintains the count members in the **ADAPTERCOUNTER** structures that make up the **ADAPTERPERFDATA** structure, incrementing the count member whenever data is received, connections fail, and other events occur. The Perfmon application accesses these counters to display Host Integration Server performance monitoring data statistics.