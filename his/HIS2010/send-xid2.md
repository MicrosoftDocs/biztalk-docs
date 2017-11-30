---
title: "Send-XID2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0aaa8aa1-7d1b-48d2-ac67-cc35f1e4fd61
caps.latest.revision: 3
---
# Send-XID
Flow : NODE ------> DLC (link connection)  
  
### Header  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|nxtqptr|PTRBFHDR|Pointer to next buffer header in a queue|  
|hdreptr|PTRBFELT|Pointer to first buffer element|  
|numelts|CHAR|Number of buffer elements|  
|msgtype|CHAR|Message type: DLCSTAT (0x11)|  
|srcl|CHAR|Source locality|  
|srcp|CHAR|Source partner|  
|srci|INTEGER|Source index|  
|destl|CHAR|Destination locality|  
|destp|CHAR|Destination partner|  
|desti|INTEGER|Destination index|  
|dshdr.dstype|CHAR|Status type: SENDXID (0x1A)|  
|dshdr.dsqual|CHAR|Station address on XID|  
  
### Element  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|hdreptr–>elteptr|PTRBFELT|Pointer to next buffer element: (NULL is only one element)|  
|hdreptr–>startd|INTEGER|Index to start of data in this buffer element's data array: 1|  
|hdreptr–>endd|INTEGER|Index to last byte of data in this buffer element's data array|  
|hdreptr–>dataru|CHAR[SNANBEDA]|Defined as follows, where s = startd–1|  
|dataru[s..s+n–1]|Not applicable|XID information frame|  
  
 Note that the **dshdr.dsqual** field is valid only for primary multipoint connections where station is specified on a multidrop line that the XID should be sent to. In all other cases, it is set to 0xFF.  
  
 In situations where the link protocol requires the address field on the XID to be set to a value other than 0xFF (for example, to specify that the XID is a response), it is the responsibility of the link service to set this byte appropriately.  
  
 The **Send-XID** message can contain zero elements (**numelts** = 0) or a single, empty element (**hdreptr–>startd** \<          **hdreptr–>endd**). In these cases, the link service is expected to transmit a NULL XID.