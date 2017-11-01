---
title: "Open(LINK) Request1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0b3a13e-ccd9-4294-bba6-be6f210cb7b0
caps.latest.revision: 3
---
# Open(LINK) Request
Flow : NODE ------> DLC  
  
### Header  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|**nxtqptr**|PTRBFHDR|Pointer to next buffer header in a queue.|  
|**hdreptr**|PTRBFELT|Pointer to first buffer element.|  
|**numelts**|CHAR|Number of buffer elements: 1 (Number of elements can be 2 if the connection is for an X.25 SVC).|  
|**msgtype**|CHAR|Message type: OPENMSG (0x01).|  
|**srcl**|CHAR|Source locality.|  
|**srcp**|CHAR|Source partner.|  
|**srci**|INTEGER|Source index.|  
|**destl**|CHAR|Destination locality.|  
|**destp**|CHAR|Destination partner.|  
|**desti**|INTEGER|Destination index.|  
|**ophdr.openqual**|CHAR|Open qualifier: REQU (0x01).|  
|**ophdr.opentype**|CHAR|Open type: LINK (0x10).|  
|**ophdr.opresid**|INTEGER|Resource identifier.|  
  
### Element 1  
  
|Field|Type|Description|  
|-----------|----------|-----------------|  
|**hdreptr–>elteptr**|PTRBFELT|Pointer to optional second buffer element (NULL if only one element).|  
|**hdreptr–>startd**|INTEGER|Index to start of data in this buffer element's data array.|  
|**hdreptr–>endd**|INTEGER|Index to last byte of data in this buffer element's data array.|  
|**hdreptr–>dataru**|CHAR[SNANBEDA]|Defined as follows, where  s = startd–1|  
|**dataru[s..s+9]**|Not applicable|Source name — name of local node.|  
|**dataru[s+10..s+19]**|Not applicable|Destination name—name of remote PU (blank for incoming calls).|  
|**dataru[s+20..s+21]**|Not applicable|Link index.|  
  
 **Link Data (depends on DLC type)**  
  
 Unless otherwise stated, these fields are valid for outgoing calls only.  
  
|SDLC link data field|Description|  
|--------------------------|-----------------|  
|**dataru[s+22]**|XID supplied 0x00 Do not send initial XID 0x01 Send initial XID from this message (may be a NULL XID)|  
|**dataru[s+23]**|Link operational role 0x00 Primary 0x01 Secondary 0x02 Negotiable|  
|**dataru[s+24]**|Use Reject_Command indicator 0x00 Do use it 0x01 Do not use it|  
|**dataru[s+25]**|Address match byte 0x00 Primary/Negotiable SDLC 0x01 to 0xFE Secondary SDLC|  
|**dataru[s+26]**|Second SDLC address match byte 0x00 Primary SDLC 0xFF Secondary/Negotiable SDLC|  
|**dataru[s+27]**|Reserved|  
  
|Channel adapter link data|Description|  
|-------------------------------|-----------------|  
|**dataru[s+22]**|XID supplied. 0x00 Do not send initial XID. 0x01 Send initial XID from this message (may be a NULL XID).|  
|**dataru[s+23]**|PU emulation type. 0x00 Unknown. 0x20 PU 2.0 (format 0 XID). 0x21 PU 2.1 (format 3 XID).|  
|**dataru[s+24]**|Control Unit Image number (0 to 15) on the Channel address configured in SNA Manager.|  
|**dataru[s+25]**|Channel subaddress.|  
|**dataru[s+26..s+67]**|Reserved (may not be zero).|  
  
|Station timers|Description|  
|--------------------|-----------------|  
|**dataru[s+28..s+29]**|Contact time-out.|  
|**dataru[s+30..s+31]**|Contact retry limit.|  
|**dataru[s+32..s+33]**|Discontact time-out.|  
|**dataru[s+34..s+35]**|Discontact retry limit.|  
|**dataru[s+36..s+37]**|Negative poll time-out.|  
|**dataru[s+38..s+39]**|Negative poll retry limit.|  
|**dataru[s+40..s+41]**|T1 (no acknowledgment) time-out.|  
|**dataru[s+42..s+43]**|T2 (acknowledgment) time-out.|  
|**dataru[s+44..s+45]**|Remote station busy time-out.|  
|**dataru[s+46..s+47]**|Remote station busy retry limit.|  
  
|Link timers|Description|  
|-----------------|-----------------|  
|**dataru[s+48..s+49]**|Idle time-out.|  
|**dataru[s+50..s+51]**|Idle retry limit.|  
|**dataru[s+52..s+53]**|Nonproductive receive time-out.|  
|**dataru[s+54..s+55]**|Nonproductive receive retry limit.|  
|**dataru[s+56..s+57]**|Write time-out.|  
|**dataru[s+58..s+59]**|Write retry limit.|  
|**dataru[s+60..s+61]**|Link connection time-out.|  
|**dataru[s+62..s+63]**|Link connection retry limit. 0xFFFF for infinite retry.|  
|**dataru[s+64..s+65]**|Reserved.|  
|**dataru[s+66]**|Configuration options: Bit 0 :    1 = Constant carrier selected Bit 1 :    1 = NRZI 0 = NRZ Bit 2 :    = Reserved Bit 3 :    1 = Full-duplex 0 = Half-duplex Bit 4 :    0 = External clocking Bit 5 :    1 = Data signal rate select high 0 = Data signal rate select low Bit 6 :    1 = Select standby on 0 = Select standby off Bit 7 :    = Reserved|  
|**dataru[s+67]**|Configuration options: line type 0x00 leased 0x01 switched manual dial 0x02 switched auto-dial|  
  
 Note that for configuration options, bit 0 is the most significant option and bit 7 is the least significant. Reserved bits are not always zero, so always use a bitwise **AND** operation when testing these bits.  
  
 The configuration options byte is also valid for incoming calls.  
  
## In This Section  
  
-   [Expanded Information About Message Formats for Open(LINK) Request with SDLC](../core/expanded-information-about-message-formats-for-open-link-request-with-sdlc.md)  
  
-   [Optional Second Element (Only Used by X.25 SVC)](../core/optional-second-element-only-used-by-x-25-svc.md)