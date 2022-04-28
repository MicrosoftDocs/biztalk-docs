---
description: "Learn more about: Open(STATION) OResponse"
title: "Open(STATION) OResponse1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c49f3b3-f6ee-4ca6-b053-2f8651f17911
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Open(STATION) OResponse
Flow : DLC ------> NODE  
  
### Header  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|nxtqptr|PTRBFHDR|Pointer to next buffer header in a queue|  
|hdreptr|PTRBFELT|Pointer to first buffer element|  
|numelts|CHAR|Number of buffer elements: 1|  
|msgtype|CHAR|Message type: OPENMSG (0x01)|  
|srcl|CHAR|Source locality|  
|srcp|CHAR|Source partner|  
|srci|INTEGER|Source index|  
|destl|CHAR|Destination locality|  
|destp|CHAR|Destination partner|  
|desti|INTEGER|Destination index|  
|ophdr.openqual|CHAR|Open qualifier: RSPOK (0x02)|  
|ophdr.opentype|CHAR|Open type: STAT (0x11)|  
|ophdr.opresid|INTEGER|Resource identifier|  
|ophdr.icreditr|INTEGER|Initial Credit for flow DLC –> NODE|  
|ophdr.icredits|INTEGER|Initial Credit for flow NODE –> DLC|  
  
### Element  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|hdreptr–>elteptr|PTRBFELT|Pointer to next buffer element (NULL is only one element)|  
|hdreptr–>startd|INTEGER|Index to start of data in this buffer element's data array: 1|  
|hdreptr–>endd|INTEGER|Index to last byte of data in this buffer element's data array|  
|hdreptr–>dataru|CHAR[SNANBEDA]|Defined as follows, where s = startd–1|  
|dataru[s..s+9]|Not applicable|Source name—same as destination name from **Open(STATION) Request**|  
|dataru[s+10..s+19]|Not applicable|Destination name—name of local node; same as source name from **Open(STATION) Request**|
