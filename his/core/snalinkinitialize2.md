---
description: "Learn more about: SNALinkInitialize"
title: "SNALinkInitialize2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
