---
title: "Link Alert Format and Common Subvectors2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03411b99-b695-4b4e-bc31-9e9e765a3c16
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Link Alert Format and Common Subvectors
The general format of link alerts is as follows:  
  
```  
NMVT HEADER  
41 03 8D 00 00 00 00 00     NMVT Header  
Major Vector Header  
LL LL     Length of Major Vector  
00 00     Alert major vector  
  
```  
  
 The specific alert is identified by the alert description and alert ID (part of the generic alert subvector). Common subvectors are listed later in this section. SDLC and Token Ring failure alerts are described in the [SDLC Failure Alerts](../core/sdlc-failure-alerts2.md) and [Token Ring Failure Alerts](../core/token-ring-failure-alerts1.md).  
  
 Each subvector or subfield begins with a 1-byte length field and a 1-byte key identifying the subvector or subfield. The length field contains the length in bytes of the entire subvector or subfield, including the length and key bytes. Where the length byte is shown as LL (record length field), this indicates that the length is not fixed because different alerts require different data to be included.  
  
 The following table lists all the possible subvectors used in the alert, with their subvector keys (identifiers).  
  
### Link alert subvectors  
  
|Subvector key (identifier)|Subvector|  
|----------------------------------|---------------|  
|05|Hierarchy/Resource List Subvector|  
|03|Hierarchy Name List Subvector|  
|01|Date/Time Subvector|  
|10|Product Set ID Subvector (this appears twice, as Alert Sender PSID and Indicated Resource PSID).|  
|51|LAN LCS Data Subvector|  
|52|LCS Configuration Data Subvector|  
|8C|Link Station Data Subvector|  
|91|Basic Alert Subvector|  
|92|Generic Alert Subvector|  
|93|Probable Cause Subvector|  
|94|User Causes Subvector|  
|95|Install Causes Subvector|  
|96|Failure Causes Subvector|  
|A1|Detail Qualifier Subvector|  
  
 The following tables describe the formats of link alert subvectors. Additional tables, in this section describe the individual link alerts.  
  
### Hierarchy/resource list subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|LL 05|Hierarchy/Resource List Subvector|  
|LL 10|Hierarchy/Resource List Subfield|  
|*hh*|Flags: 80 (1-User) 00 (Server)|  
|LL|Name field length: name length plus this length byte.|  
|*hh...hh*|Adapter name in EBCDIC, 8 bytes|  
|00|Flags byte: always 0|  
|3F|Resource type: port|  
|Optional second name|Remote host name. For Token Ring, use the local ring name. See the individual alert descriptions found later in this section.|  
|LL|Name field length: name length plus this length byte.|  
|*hh...hh*|Name in EBCDIC, up to 8 bytes|  
|00|Flags byte: always 0|  
|F4 or 2E|Resource type: control point or Token Ring.|  
  
### Hierarchy/name list subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|LL 03|Hierarchy Name List subvector|  
|00 or 03|Reserved byte|  
|*hh*|Number of names in the hierarchy name list.|  
|LL|Length of each name, including this length byte.|  
|*hh...hh*|Name of resource for each name.|  
|D3 C3 D6 D5|Resource type identifier: LCON (logical link connection not known to SNA)|  
  
### Date/time subvector alerts  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|0A 01|Date/Time Subvector|  
|08 10|Local Date/Time subfield|  
|*hh*|Year  two digits|  
|*hh*|Month|  
|*hh*|Date|  
|*hh*|Hours|  
|*hh*|Minutes|  
|*hh*|Seconds (binary)|  
  
### Product set ID subvector  
  
|                Format and contents                 |                                              Description                                               |
|----------------------------------------------------|--------------------------------------------------------------------------------------------------------|
|                       2A 10                        |                                        Product Set ID subvector                                        |
|                         00                         |                                             (unused field)                                             |
|                       27 11                        |                                          Product ID subvector                                          |
|                         0C                         |                                Product classification: non-IBM software                                |
|                       08 04                        |                                 Software product common level subfield                                 |
|                       F0 F2                        |                                         Version identifier: 02                                         |
|                       F0 F0                        |                                         Release identifier: 00                                         |
|                       F0 F0                        |                                      Modification identifier: 00                                       |
|                       13 06                        |                                 Software product common name subfield                                  |
| C4 C3 C1 61 D4 E2 40 C3 D6 D4 D4 40 E2 C5 D9 E5 D9 | Product name: Microsoft [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] |
|                       09 08                        |                                Software product program number subfield                                |
|                F0 F0 F0 F0 F0 F0 F0                |                                     Product program number: zeros                                      |
  
### LAN link connection subsystem data subvector*  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|LL 51|LAN LCS Data Subvector|  
|04 02|Ring Identifier subfield|  
|*hh hh*|Ring number|  
|08 03|Local Individual MAC Address subfield|  
|*hh...hh*|Local individual MAC address|  
|08 04|Remote Individual MAC Address subfield|  
|*hh...hh*|Remote individual MAC address|  
|LL 05|LAN Routing Information subfield|  
|*hh...hh*|LAN routing information|  
  
 \* Token ring only.  
  
### Link connection subsystem configuration data subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|LL 52|LCS Configuration Data Subvector|  
|04 01|Port Address subfield|  
|*hh hh*|Port address|  
|03 02|Remote Device Address subfield|  
|*hh*|Remote device address|  
|03 04|Local Device Address subfield|  
|*hh*|Local device address|  
|04 06|Link Station Attributes subfield|  
|01 or 02 or 03|Link station role: Primary, Secondary, or Negotiable|  
|03 or 04|Remote node type: Type 4 or Type 2.1|  
|06 07|Link Attributes subfield|  
|01 or 02|Link connection type: nonswitched or switched|  
|01 or 02|Half-duplex or full-duplex|  
|01|Protocol: SDLC|  
|01 or 02|Point-to-point or multipoint|  
  
### Link station data subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|LL 8C|Link Station Data Subvector|  
|04 01|N(s) and N(r) counts subfield|  
|*hh*|N(s) count|  
|*hh*|N(r) count|  
|03 02|Outstanding frame count subfield|  
|*hh*|Outstanding frame count|  
|04 03|Last SDLC Control Field Received subfield|  
|*hh* *hh*|Last control field received|  
|04 04|Last SDLC Control Field Sent subfield|  
|*hh* *hh*|Last control field sent|  
|03 05|Sequence Number Modulus subfield|  
|80|Sequence number modulus|  
|03 06|Link Station State subfield|  
|80 or 40|Link station state: local or remote station sending RNR|  
|04 07|LLC Reply Timer Expiration Count subfield|  
|*hh* *hh*|Reply timer expiration count|  
|03 08|Last Received N(r) Count subfield|  
|*hh*|Last received N(r) (binary)|  
  
### Basic alert subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|0E 91|Basic Alert subvector|  
|00|Not-operator initiated|  
|01|Alert type: permanent|  
|0E|General cause code: link-level protocol error|  
|00 80 or 00 34|Specific component code: Token Ring LAN or SDLC data link control|  
|00 00|Alert description code|  
|00 00|User action code|  
|00 00|Detail text reference code|  
|00|Unused field|  
  
### Generic alert subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|0B 92|Generic Alert subvector|  
|00 00|Flags: not operator-initiated, not a held alert|  
|01|Alert type: permanent|  
|*hh* *hh*|Alert description: See alert descriptions.|  
|*hh* *hh* *hh* *hh*|Alert ID number (unique to a particular alert)|  
  
### Probable cause subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|LL 93|Probable cause subvector|  
|*hh* *hh*|Probable cause: See individual alert descriptions. This alert may include more than one entry.|  
  
### User causes subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|LL 94|User Causes Subvector|  
|LL 01|User causes subfield|  
|*hh* *hh*|User cause: See individual alert descriptions. More than one entry may appear here.|  
|LL 81|Recommended actions subfield|  
|*hh* *hh*|Recommended action: See individual alert descriptions. More than one entry may appear here.|  
|03 83|Product set ID index subfield|  
|99|Product Set ID index|  
|LL 82|Detailed data subfield. This subfield may appear more than once.|  
|99|Product Set ID code|  
|*hh*|Data ID: See individual alert descriptions.|  
|00|Data encoding: hexadecimal|  
|*hh*...*hh*|Detailed data: See individual alert descriptions.|  
  
### Install cause subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|LL 95|Install Causes Subvector|  
|LL 01|Install causes subfield|  
|*hh* *hh*|Install cause: See individual alert descriptions. More than one entry may appear here.|  
|LL 81|Recommended actions subfield|  
|*hh* *hh*|Recommended action: See individual alert descriptions. More than one entry may appear here.|  
|03 83|Product set ID index subfield|  
|99|Product Set ID index|  
|LL 82|Detailed data subfield. This subfield may occur more than once.|  
|99|Product Set ID code|  
|*Hh*|Data ID: See individual alert descriptions.|  
|00|Data encoding: hexadecimal|  
|*Hh*...*hh*|Detailed data: See individual alert descriptions.|  
  
### Failure cause subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|LL 96|Failure Causes Subvector|  
|LL 01|Failure causes subfield|  
|*hh* *hh*|Failure cause: See individual alert descriptions. More than one entry may appear here.|  
|LL 81|Recommended actions subfield|  
|*hh* *hh*|Recommended action: See individual alert descriptions. More than one entry may appear here.|  
|03 83|Product set ID index subfield|  
|99|Product Set ID index|  
|LL 82|Detailed data subfield. This subfield may occur more than once.|  
|99|Product Set ID code|  
|*hh*|Data ID: See individual alert descriptions.|  
|00|Data encoding: hexadecimal|  
|*hh*...*hh*|Detailed data: See individual alert descriptions.|  
  
### Detail qualifier (hexadecimal) subvector  
  
|Format and contents|Description|  
|-------------------------|-----------------|  
|06 A1|Detail Qualifier subvector|  
|*hh* *hh* *hh* *hh*|Detail Qualifier subfield  four bytes as follows:<br /><br /> Token ring: adapter number<br /><br /> Alert number<br /><br /> Two-byte error code SDLC: link ID<br /><br /> Station address, outage|  
  
## See Also  
 [Link Alerts for SDLC and Token Ring](../core/link-alerts-for-sdlc-and-token-ring2.md)