---
title: "SNALink Initialization1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b24d1b4b-cca1-4be0-bc70-36c69e1a2832
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNALink Initialization
When the SNALink is loaded into memory, the Base/DMOD performs all initialization required by the Host Integration Server system, including announcing availability of the new SNALink to other Host Integration Server components.  
  
 When this has been completed, the Base/DMOD calls the [SNALinkInitialize](./snalinkinitialize2.md) function, which must be provided by the IHV link support code.  
  
 **SNALinkInitialize** is called with a parameter that is a handle to the global Base event. This handle should be saved by the SNALink and used to signal the Base when an event occurs (for example, when data is received from the link).  
  
 The **SNALinkInitialize** function should also:  
  
- Read in the Host Integration Server configuration information for the SNALink. For details, see [SNALink Configuration Information](../core/snalink-configuration-information1.md).  
  
- Set up any required data structures.  
  
- Register with the driver that provides the support for the hardware adapter, initializing this if necessary.  
  
  If initialization fails for any reason (for example, if an associated driver is not installed), the function should report the failure to the administrator by calling **SNAReportStatus**.