---
title: "DLC-Data2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f3defbc-70f6-4bf6-8e94-cf7d2133e0d1
caps.latest.revision: 3
---
# DLC-Data
Flow : DLC \<------> NODE  
  
### Header  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|nxtqptr|PPTRBFHDR|Pointer to next buffer header in a queue|  
|hdreptr|PPTRBFELT|Pointer to first buffer element|  
|numelts|CCHAR|Number of buffer elements|  
|msgtype|CCHAR|Message type: DLCDATA (0x10)|  
|srcl|CCHAR|Source locality|  
|srcp|CCHAR|Source partner|  
|srci|INTEGER|Source index|  
|destl|CCHAR|Destination locality|  
|destp|CCHAR|Destination partner|  
|desti|INTEGER|Destination index|  
|ddhdr.ddth01|CCHAR[6]|Transmission header|  
  
### Element  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|hdreptr–>elteptr|PPTRBFELT|Pointer to next buffer element: (NULL is only one element)|  
|hdreptr–>startd|INTEGER|Index to start of data in this buffer element's data array: 1|  
|hdreptr–>endd|INTEGER|Index to last byte of data in this buffer element's data array|  
|hdreptr–>dataru|CHAR[SNANBEDA]|Defined as follows, where s = startd–1|  
|dataru[s..s+n–1]|Not applicable|SNA request/response header (RH) if present, and request/response unit (RU) if not present|