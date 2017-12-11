---
title: "Outage1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e292935b-c567-4430-b7ce-3130e674f082
caps.latest.revision: 3
---
# Outage
Flow : DLC ------> NODE (link or station connection)  
  
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
|dshdr.dstype|CHAR|Status type: OUTAGE (0x18)|  
|dshdr.dsqual|CHAR|Outage qualifier|  
|dshdr.dsoutsq|CHAR|Outage subqualifier (optional)|  
  
 Note the following:  
  
-   This message contains a buffer header only.  
  
-   Outage qualifier codes are given in [Outages](../HIS2010/outages-snadis-1.md).