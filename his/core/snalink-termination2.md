---
title: "SNALink Termination2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adda8ba9-989d-4a24-9153-e6bc2633f227
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNALink Termination
When a critical error occurs, forcing abnormal termination of the SNALink, the IHV code must ensure that all active connections are cleanly terminated, using whatever protocols are appropriate for the link type in use. For example, an X.25 SNALink would send a CLEAR packet on all active VCs and possibly take down level 2.  
  
 This should be performed using the process detach facility of the Win32® API function **DLLEntryPoint** .