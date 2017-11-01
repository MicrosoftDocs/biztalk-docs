---
title: "MsSna_Connection8022Dlc Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40ed2db8-e83c-4537-ab5f-54723dc57df7
caps.latest.revision: 4
---
# MsSna_Connection8022Dlc Class
Describes a type of SNA connection that uses DLC 802.2 protocol over a Token Ring or Ethernet.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_Connection8022Dlc : MsSna_Connection  
{  
   String Address;  
   sint16 DlcRetryLimit;  
   sint16 DlcTimerT1;  
   sint16 DlcTimerT2;  
   sint16 DlcXidRetry;  
   sint16 DlcRecvThresh;  
   sint16 DlcSendLimit;  
   sint16 DlcRemoteSAP;  
   sint16 DLCType;  
   sint16 DlcLocalSAP;  
   sint32 MaxBtu;  
};  
```  
  
#### Parameters  
 **Address**  
 Data Type: **String** Qualifiers: **MAXLEN(12), TOUPPERCASE** Access Type: Read/Write  
  
 The 12-digit hexadecimal remote network address. You can receive the correct value for **Address** by contacting the administrator of the remote system.  
  
 **DlcRetryLimit**  
 Data Type: **sint16** Qualifiers: **MINVALUE(0), MAXVALUE(255)** Access Type: Read/Write  
  
 The number of times that the local system should retransmit a frame if no response is received from the remote system.  
  
 **DlcTimerT1**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The amount of time that the local system should wait for the remote system to respond to a transmission before the local system tries again. The following table describes the possible values for **DlcTimer**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Default|  
|1|200 ms|  
|2|400 ms|  
|3|600 ms|  
|4|800 ms|  
|5|1000 ms|  
|6|1 s|  
|7|2 s|  
|8|3 s|  
|9|4 s|  
|10|5 s|  
  
 **DlcTimerT2**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The maximum amount of time that should be allowed before the local system sends an acknowledgment of a received transmission. The following table describes the possible values for **DlcTimerT2**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Default|  
|1|40 ms|  
|2|80 ms|  
|3|120 ms|  
|4|160 ms|  
|5|200 ms|  
|6|400 ms|  
|7|800 ms|  
|8|1200 ms|  
|9|1600 ms|  
|10|2000 ms|  
  
 **DlcXidRetry**  
 Data Type: **sint16** Qualifiers: **QualiferValueHere** Access Type: Read/Write  
  
 The amount of time that the link can be inactive before the local system treats it as nonfunctioning and shuts it down. The following table describes the possible values for **DlcXidRetry**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|1 s|  
|1|2 s|  
|2|3 s|  
|3|4 s|  
|4|5 s|  
|5|5 s (2)|  
|6|10 s|  
|7|15 s|  
|8|20 s|  
|9|25 s|  
  
 **DlcXidRetry**  
 Data Type: **sint16** Qualifiers: **MINVALUE(0), MAXVALUE(30)** Access Type: Read/Write  
  
 The number of times that the local system should retransmit an XID, an identifying message, if no response is received from the remote system.  
  
 **DlcRecvThresh**  
 Data Type: **sint16** Qualifiers: **MINVALUE(0), MAXVALUE(127)** Access Type: Read/Write  
  
 The maximum number of frames that the local system can receive from the remote system before sending a response.  
  
 **DlcSendLimit**  
 Data Type: **sint16** Qualifiers: **MINVALUE(0), MAXVALUE(127)** Access Type: Read/Write  
  
 The maximum number of frames that the local system can send without receiving a response from the remote system.  
  
 **DlcRemoteSAP**  
 Data Type: **sint16** Qualifiers: **MINVALUE(4), MAXVALUE(252)** Access Type: Read/Write  
  
 A 2-digit hexadecimal number that is a multiple of 04, between 04 and EC. See your Token Ring or Ethernet manual for more information.  
  
 **DLCType**  
 Data Type: **sint16** Access Type: Read-Only  
  
 The DLC type. The following table describes the possible values for **DLCType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Token|  
|1|Ether|  
  
 **DlcLocalSAP**  
 Data Type: sint16 Qualifiers: **MINVALUE(4), MAXVALUE(252)** Access Type: Read/Write  
  
 A 2-digit hexadecimal number that is a multiple of 04, between 04 and EC. See your Token Ring or Ethernet manual for more information.  
  
 **MaxBtu**  
 Data Type: **sint16** Qualifiers: **MINVALUE(265), MAXVALUE(16393)** Access Type: Read/Write  
  
 The maximum Basic Transmission Unit (BTU) Length.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes.md)   
 [Administration and Management Programmer's Guide](../Topic/Administration%20and%20Management%20Programmer's%20Guide1.md)