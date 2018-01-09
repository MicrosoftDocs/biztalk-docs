---
title: "Request-Open-Station2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 028dd1de-2965-4865-a400-34d1353d9f45
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Request-Open-Station
Flow : DLC ------> NODE (link connection)  
  
### Header  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|nxtqptr|PTRBFHDR|Pointer to next buffer header in a queue|  
|hdreptr|PTRBFELT|Pointer to first buffer element if present|  
|numelts|CHAR|Number of buffer elements|  
|msgtype|CHAR|Message type: DLCSTAT (0x11)|  
|srcl|CHAR|Source locality|  
|srcp|CHAR|Source partner|  
|srci|INTEGER|Source index|  
|destl|CHAR|Destination locality|  
|destp|CHAR|Destination partner|  
|desti|INTEGER|Destination index|  
|dshdr.dstype|CHAR|Status type: QOPNSTN (0x16)|  
|dshdr.dsqual|CHAR|Station address on XID or mode-set command. Set to 0x01 for 802.2|  
|dshdr.dsmdset|CHAR|Rcv-Set-Mode flag 0x00 XID received 0x01 Mode set command received for example, SNRM for SDLC SABME for 802.2 QSM for X.25|  
  
|Element field|Type|Description|  
|-------------------|----------|-----------------|  
|hdreptr–>elteptr|PTRBFELT|Pointer to next buffer element (NULL is only one element)|  
|hdreptr–>startd|INTEGER|Index to start of data in this buffer element's data array: 1|  
|hdreptr–>endd|INTEGER|Index to last byte of data in this buffer element's data array|  
|hdreptr–>dataru|CHAR[SNANBEDA]|Defined as follows, where s = startd–1|  
|dataru[s..s+n–1]|Not applicable|XID-starting at first byte of received XID information field. 0x00 NULL XID received (n = 1) and signaling information present.|  
  
### Optional Signaling Information  
  
|Field|Description|  
|-----------|-----------------|  
|dataru[s+n]|Length of data, including this byte|  
|dataru[s+n+1]|Type of data (not used at present)|  
|dataru[s+n+2..s+m]|Address or other identifier data. For example, media access control (MAC) address of remote station X.25 address of remote station|  
  
-   The signaling information is used by the node to identify the remote station on 802.2 and X.25 links.  
  
> [!NOTE]
>  If a NULL XID is received and no signaling information is required, the element can be omitted.  
  
> [!NOTE]
>  If a NULL XID is received and signaling information is required, an 0x00 byte should be put in the element followed by the signaling information.  
  
> [!NOTE]
>  If the Rcv-Set-Mode flag is set to 0x01, the element can be omitted.