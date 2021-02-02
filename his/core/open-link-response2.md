---
description: "Learn more about: Open(LINK) Response"
title: "Open(LINK) Response2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e386f81-f45b-40e5-861e-e10b70322329
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Open(LINK) Response
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
|ophdr.openqual|CHAR|Open qualifier  - RSPOK (0x02)  - RSPERR (0x03)|  
|ophdr.opentype|CHAR|Open type  - LINK (0x10)|  
|ophdr.opresid|INTEGER|Resource identifier|  
|ophdr.operr1|INTEGER|Error code (see immediately following the table)|  
|ophdr.operr2|INTEGER|Reserved|  
|hdreptr–>elteptr|PTRBFELT|Pointer to next buffer element: NULL|  
|hdreptr–>startd|INTEGER|Index to start of data in this buffer element's data array: 1|  
|hdreptr–>endd|INTEGER|Index to last byte of data in this buffer element's data array|  
|hdreptr–>dataru|CHAR[SNANBEDA]|Defined as follows, where s = startd–1|  
|dataru[s..s+9]|Not applicable|Source name—same as destination name from **Open(LINK) Request**|  
|dataru[s+10..s+19]|Not applicable|Destination name—name of local node; same as source name from **Open(LINK) Request**|  
|dataru[s+22..s+23]|Not applicable|The maximum BTU size supported by SNALink. This size is 65,536 (largest number in an unsigned short) for channel connections and 32,768 for non-channel connections.<br /><br /> Note that this limit does not guarantee that the SNA connection will actually use this value. The individual link service or the host can negotiate it downward.|  
  
 The error codes (for an ERROR-RESPONSE) are defined as follows in SNA_CNST.H:  
  
|Symbolic constant|Value|Description|  
|-----------------------|-----------|-----------------|  
|ERINIFAIL|0x01|Hardware initialization failed|  
|ERINVXID|0x08|Invalid XID length|  
|ERLINKOPN|0x09|Link already open|  
|ERLLCERR|0x0A|LCC error; fatal hardware failure|  
|ERBADINDX|0x0B|Invalid link index|  
|ERBADOPN|0x0C|**Open(LINK)** has insufficient data|  
|ERCONNTO|0x0D|Link connection time-out|  
|ERNORES|0x0E|Maximum connection count reached                      –or– No more internal control blocks|  
|EROPNPND|0x11|**Close(LINK)** arrived while **Open(LINK)** pending|  
|ERDUPREQ|0x12|Duplicate request|
