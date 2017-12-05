---
title: "Required Exports1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bec5a572-06e4-444a-8d9c-7379ae187236
caps.latest.revision: 3
---
# Required Exports
The IHV link support DLL must export the following entry points:  
  
-   [SNALinkInitialize](../HIS2010/snalinkinitialize1.md)  
  
-   [SNALinkWorkProc](../HIS2010/snalinkworkproc2.md)  
  
-   [SNALinkDispatchProc](../HIS2010/snalinkdispatchproc1.md)  
  
 These are called by the Base scheduler when the SNALink is invoked.