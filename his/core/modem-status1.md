---
description: "Learn more about: MODEM_STATUS"
title: "MODEM_STATUS1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a03fcbc8-000c-4266-ae44-edcf82fa4bcb
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# MODEM_STATUS
A **MODEM_STATUS** structure for each SNA link contains status information used by the SNA Modem Status interface.  
  
## Syntax  
  
```  
  
struct _ModemStatus{  
....char LSName[12];  
    char V24In;  
    char V24Out;  
    unsigned short RxFrameCount;  
    unsigned short TxFrameCount;  
    char Reserved[6];  
} MODEM_STATUS;  
```  
  
## Remarks  
  
## Members  
 **LSName**  
 A character array containing the link service name.  
  
 **V24In**  
 A set of bit fields representing the V.24 input flags that determine which signal lines to mask. These bit fields can be joined with **OR** to create a complete mask. The defined bit fields for **V24In** are as follows:  
  
 MASK_CTS  Mask the clear to send line.  
  
 MASK_DSR  Mask the data set ready line.  
  
 MASK_DCD  Mask the data carrier detect line.  
  
 MASK_DRI  Mask the data ring indicator line.  
  
 **V24Out**  
 A set of bit fields representing the V.24 output flags that determine which signal lines to mask. These bit fields can be joined with **OR** to create a complete mask. The defined bit fields for **V24Out** are as follows:  
  
 MASK_RTS  Mask the request to send line.  
  
 MASK_DTR  Mask the data terminal ready line.  
  
 **RxFrameCount**  
 A count of received frames.  
  
 **TxFrameCount**  
 A count of transmitted frames.  
  
 **Reserved**  
 Padding for future expansion.
