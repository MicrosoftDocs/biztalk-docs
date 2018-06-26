---
title: "Required Exports2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b18eeae-8ab6-4577-bfdb-8c97a9fa8de7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Required Exports
The IHV link support DLL must export the following entry points:  
  
- [SNALinkInitialize](./snalinkinitialize2.md)  
  
- [SNALinkWorkProc](./snalinkworkproc1.md)  
  
- [SNALinkDispatchProc](./snalinkdispatchproc2.md)  
  
  These are called by the Base scheduler when the SNALink is invoked.