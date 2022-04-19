---
description: "Learn more about: SNALinkInitialize"
title: "SNALinkInitialize2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8a1b65b-1147-41ce-859b-4ec824610540
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
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
