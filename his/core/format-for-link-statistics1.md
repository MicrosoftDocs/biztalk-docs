---
description: "Learn more about: Format for Link Statistics"
title: "Format for Link Statistics1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa707f7d-bd2f-452b-9a35-d7c99c017d8e
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Format for Link Statistics
When an SDLC or Token Ring connection ends, or when an error counter reaches its maximum value, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] records statistics on link usage. These statistics include information such as the adapter number, the date and time the link was established, and the counts of errors and timeouts. This data is also logged in NMVT (network management vector transport) format if a connection has been specified for carrying NetView data. The data is then sent if that connection and the server that owns the connection are both active.  
  
 This section contains:  
  
-   [SDLC Link Statistics](../core/sdlc-link-statistics1.md)  
  
-   [Token Ring Link Statistics](../core/token-ring-link-statistics2.md)
