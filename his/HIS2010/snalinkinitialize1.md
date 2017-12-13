---
title: "SNALinkInitialize1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2758e18-01ad-4219-87e7-407701309a75
caps.latest.revision: 3
---
# SNALinkInitialize
The **SNALinkInitialize** function initializes the SNALink. The Base calls this function when the SNALink is loaded into memory.  
  
```  
VOID SNALinkInitializer(  
HANDLE event   
);  
```  
  
## Parameters  
 *event*  
 A handle to the global Base event.  
  
## Remarks  
 This function should:  
  
-   Read in required configuration information.  
  
-   Perform any required initialization of the hardware or device driver.  
  
-   Set up control blocks and data structures required internally by the SNALink.