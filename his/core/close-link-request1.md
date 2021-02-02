---
description: "Learn more about: Close(LINK) Request"
title: "Close(LINK) Request1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abc0c2c2-e61b-41fd-9567-f772e826100a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Close(LINK) Request
Flow : NODE ------> DLC  
  
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
|clhdr.closqual|CHAR|Close qualifier: REQU (0x01)|  
|clhdr.clstype|CHAR|Close type: LINK (0x10)|  
  
 Note that the message consists of a buffer header only.
