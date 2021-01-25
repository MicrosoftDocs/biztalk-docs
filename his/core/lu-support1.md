---
description: "Learn more about: LU Support"
title: "LU Support1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1f1760e-9be8-420c-ab54-0796eaa522f4
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# LU Support
A [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] node can support as many as 15,000 sessions.  
  
 Logical unit 6.2 (LU 6.2) works in combination with node type 2.1 to provide Advanced Program-to-Program Communications (APPC). An LU 6.2 can be either a primary logical unit (PLU) or a secondary logical unit (SLU). The partner LU can reside in a type 2.1 node, within an upstream type 5 node, or within the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] node itself.  
  
 LU types 0, 1, 2, or 3 are always SLUs, and the partner LU in an upstream type 5 node is always the PLU. LU 0 supports session-level cryptography, within certain limits, on the Request Unit Interface (RUI). You implement session-level cryptography through Cryptography Verification (CRV) requests; the RUI applications must perform all necessary processing. For details about the limits of session-level cryptography and about the processing carried out by the RUI application, see the [LUA Programmer's Guide](./lua-programmer-s-guide1.md). For all interfaces other than RUI, CRV requests are handled with a negative response.  
  
## See Also  
 [SNA Session Support](../core/sna-session-support2.md)
