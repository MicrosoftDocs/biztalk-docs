---
title: "Open(STATION) Request2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2882690d-5435-4e27-9cea-b92368d2b86a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Open(STATION) Request
Flow : NODE ------> DLC  
  
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
|ophdr.openqual|CHAR|Open qualifier: REQU (0x01)|  
|ophdr.opentype|CHAR|Open type: STAT (0x11)|  
|ophdr.opresid|INTEGER|Resource identifier|  
|ophdr.icreditr|INTEGER|Initial credit for flow DLC –> NODE|  
  
### Element  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|hdreptr–>elteptr|PTRBFELT|Pointer to optional second buffer element (NULL if only one element)|  
|hdreptr–>startd|INTEGER|Index to start of data in this buffer element's data array: 1|  
|hdreptr–>endd|INTEGER|Index to last byte of data in this buffer element's data array|  
|hdreptr–>dataru|CHAR[SNANBEDA]|Defined as follows, where s = startd–1|  
|dataru[s..s+9]|Not applicable|Source name—name of local node|  
|dataru[s+10..s+19]|Not applicable|Destination name|  
|dataru[s+20..s+21]|Not applicable|Link index as specified in **Open(LINK) Request**|  
|dataru[s+22]|Not applicable|If NODE is primary, address of secondary station to initiate contact procedure with. 0x00 if NODE is secondary|  
|dataru[s+23]|Not applicable|FID2 indicator 0x00 FID2 used|  
|dataru[s+24]|Not applicable|Station type 0x00 Subarea 0x01 Peer|  
|dataru[s+25..s+26]|Not applicable|Length of network name from received XID 0000 = No name|  
|dataru[s+27..s+27+n]|Not applicable|Network name from received XID, in local character set, or if this is null, the name of the remote PU record in the COM.CFG file. This name can be fully qualified and has a maximum length of 17 characters.|  
|dataru[s+44..s+89]|Not applicable|Link data—a copy of that supplied on the **Open(LINK) Request**|  
|dataru[s+90..s+91]|Not applicable|The maximum BTU size to be used with this station. This size is 65,536 (largest number in an unsigned short) for channel connections and 32,768 for non-channel connections.<br /><br /> Note that this limit does not guarantee that the SNA connection will actually use this value. The individual link service or the host can negotiate it downward.|  
|dataru[s+m+1]|Not applicable|Local service access point (SAP) used by remote station. The remote SAP information is only allowed for 802.2 connections, and may only be present if Signaling information is present. It is used along with the Signaling Information to identify the remote station.|