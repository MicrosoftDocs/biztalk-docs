---
description: "Learn more about: Open(STATION) Error Response"
title: "Open(STATION) Error Response1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Open(STATION) Error Response
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
|ophdr.openqual|CHAR|Open qualifier: RSPERR (0x03)|  
|ophdr.opentype|CHAR|Open type: STAT (0x11)|  
|ophdr.opresid|INTEGER|Resource identifier|  
|ophdr.operr1|INTEGER|Error code|  
|ophdr.operr2|INTEGER|Reserved|  
  
### Element  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|hdreptr–>elteptr|PTRBFELT|Pointer to next buffer element (NULL is only one element)|  
|hdreptr–>startd|INTEGER|Index to start of data in this buffer element's data array - 1|  
|hdreptr–>endd|INTEGER|Index to last byte of data in this buffer element's data array|  
|hdreptr–>dataru|CHAR[SNANBEDA]|Defined as follows, where s = startd - 1|  
|dataru[s..s+9]|Not applicable|Source name|  
|dataru[s+10..s+19]|Not applicable|Destination name|  
  
 The error codes are defined as follows:  
  
|Symbolic constant|Value|Description|  
|-----------------------|-----------|-----------------|  
|ERLKNOTOPEN|0x03|Link not open|  
|ERSTATOPEN|0x05|Station already open|  
|ERNOCB|0x06|Station control blocks depleted|  
|ERINVINDX|0x07|Invalid link index|  
|ERMAXSTAT|0x08|Limit for number of stations per link reached|  
|ERDIFADDR|0x09|Address different from that on **Request-Open-Station**|  
|ERBADADDR|0x0A|Invalid DLC address|
