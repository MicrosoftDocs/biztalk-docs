---
description: "Learn more about: Close(STATION) Response"
title: "Close(STATION) Response1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 15ca0be5-1e84-402b-9bd2-8f044a915b64
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Close(STATION) Response
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
|clhdr.clsequal|CHAR|Close qualifier  - RSPOK (0x02)  - RSPERR (0x03)|  
|clhdr.clstype|CHAR|Close type: STAT (0x11)|  
|clhdr.clserr1|INTEGER|Error code|  
  
 The error codes (for an ERROR-RESPONSE) are defined as:  
  
-   0x03 — Station not open  
  
-   0x04 — Link not connected  
  
-   0x05 — Invalid station index  
  
-   70x06 — Duplicate request  
  
    > [!NOTE]
    >  The message consists of a buffer header only.  
  
    > [!NOTE]
    >  The Close(STATION) message unconditionally closes the station connection.
