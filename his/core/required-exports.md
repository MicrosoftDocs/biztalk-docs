---
title: "Required Exports2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b18eeae-8ab6-4577-bfdb-8c97a9fa8de7
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Required Exports
The IHV link support DLL must export the following entry points:  
  
-   [SNALinkInitialize](../Topic/SNALinkInitialize1.md)  
  
-   [SNALinkWorkProc](../Topic/SNALinkWorkProc2.md)  
  
-   [SNALinkDispatchProc](../Topic/SNALinkDispatchProc1.md)  
  
 These are called by the Base scheduler when the SNALink is invoked.