---
description: "Learn more about: Close(LINK) Response"
title: "Close(LINK) Response2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Close(LINK) Response
Flow : DLC ------> NODE  
  
### Header  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|nxtqptr|PTRBFHDR|Pointer to next buffer header in a queue|  
|hdreptr|PTRBFELT|Pointer to first buffer element: NULL|  
|numelts|CHAR|Number of buffer elements: 0|  
|msgtype|CHAR|Message type: CLOSEMSG (0x02)|  
|srcl|CHAR|Source locality|  
|srcp|CHAR|Source partner|  
|srci|INTEGER|Source index|  
|destl|CHAR|Destination locality|  
|destp|CHAR|Destination partner|  
|desti|INTEGER|Destination index|  
|clhdr.closqual|CHAR|Close qualifier  - RSPOK (0x02)  - RSPERR (0x03)|  
|clhdr.clstype|CHAR|Close type: LINK (0x10)|  
|clhdr.clserr1|INTEGER|Error code (see immediately following the table)|  
  
 The error codes (for an ERROR-RESPONSE) are defined as:  
  
-   0x03 — Link not open  
  
-   0x04 — Invalid link index  
  
> [!NOTE]
>  The **Close(LINK)** message unconditionally shuts down the link.
