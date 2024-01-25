---
description: "Learn more about: Status-Resource (SNADIS)"
title: "Status-Resource (SNADIS)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Status-Resource (SNADIS)
Flow : DLC \<------> NODE (station connection)  
  
### Header  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|nxtqptr|PTRBFHDR|Pointer to next buffer header in a queue|  
|hdreptr|PTRBFELT|Pointer to first buffer element: NULL|  
|numelts|CHAR|Number of buffer elements: 0|  
|msgtype|CHAR|Message type: DLCSTAT (0x11)|  
|srcl|CHAR|Source locality|  
|srcp|CHAR|Source partner|  
|srci|INTEGER|Source index|  
|destl|CHAR|Destination locality|  
|destp|CHAR|Destination partner|  
|desti|INTEGER|Destination index|  
|dshdr.dstype|CHAR|Status type: RESOURCE (0x04)|  
|dshdr.dlccred|INTEGER|DLC credit|  
  
> [!NOTE]
>  This message contains a buffer header only.  
  
> [!NOTE]
>  The **dlccred** field indicates that the message sender can receive a further **dlccred DLC-Data** message.
