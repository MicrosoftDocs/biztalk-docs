---
description: "Learn more about: MsSna_ConnectionSdlc Class"
title: "MsSna_ConnectionSdlc Class1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_ConnectionSdlc Class
A type of SNA connection that uses SDLC protocol over dial-up or leased lines.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ConnectionSdlc : MsSna_Connection  
{  
   String DialData;  
   sint16 SdlcEncoding;  
   sint16 SdlcDuplex;  
   String SdlcPollAddress;  
   boolean SdlcLeasedLine;     
   sint16 SdlcDataRate;  
   sint16 SdlcContactLimit;  
   sint16 SdlcContactTO;  
   sint16 SdlcIdleLimit;  
   sint16 SdlcIdleTO;  
   boolean SdlcMultiPrimary;  
   sint16 SdlcPollLimit;  
   sint16 SdlcPollTO;  
   sint16 SdlcPollRate;  
   boolean SdlcStandby;  
   sint16 SdlcSwitchTO;  
   sint32 MaxBtu;  
};  
```  
  
#### Parameters  
 **DialData**  
 Data Type: **String** Qualifiers: **MAXLEN(40)** The dial data for connections which use a switched line and the phone number is not stored in the modem.  
  
 **SdlcEncoding**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The encoding scheme (NRZ or NRZI) for the modem to use. The following table describes the possible values for **3dlcEncoding**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|NRZ|  
|1|NRZI|  
  
 **SdlcEncoding** must match the remote modem.  
  
 **SdlcDuplex**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The duplex setting of the modem. The following table describes the possible values for **SdlcDuplex**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Half|  
|1|Full|  
  
 **SdlcPollAddress**  
 Data Type: **String** Qualifiers: **MAXLEN(2)** Access Type: Read/Write  
  
 A 2-digit hexadecimal number describing the poll address. Contact the administrator of the remote system to determine the appropriate value.  
  
 **SdlcLeasedLine**  
 Data Type: **Boolean** Access Type: Read-Only  
  
 The value depends on the Link service.  
  
 **SdlcDataRate**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The data rate for transmissions between the communications adapter and the modem. The following table describes the possible values for **SdlcDataRate**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Low|  
|1|High|  
  
 **SdlcContactLimit**  
 Data Type: **String** Qualifiers: **MINVALUE(1), MAXVALUE(20)** Access Type: Read/Write  
  
 The maximum number of times the link service resends an XID or SNRM before declaring an outage to Host Integration Server.  
  
 **SdlcContactTO**  
 Data Type: **String** Qualifiers: **MINVALUE(5), MAXVALUE(300)** Access Type: Read/Write  
  
 The length of time, in tenths of a second, which the SDLC link service waits for an XID or SNRM response before resending the XID or SNRM.  
  
 **SdlcIdleLimit**  
 Data Type: **sint16** Qualifiers: **MINVALUE(1), MAXVALUE(255)** Access Type: Read/Write  
  
 The number of times for the local system to try to send data to the remote system if there is no response.  
  
 **SdlcIdleTO**  
 Data Type: **sint16** Access Type: **MINVALUE(1), MAXVALUE(300)**  
  
 The length of time, in tenths of a second, for the local system to wait for a response to a transmission before trying again.  
  
 **SdlcMultiPrimary**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate this is a leased SDLC line to downstream systems, and this server will be the primary station for a multidrop connection; otherwise, **false**.  
  
 **SdlcPollLimit**  
 Data Type: **sint16** Qualifiers: **MINVALUE(1), MAXVALUE(255)** Access Type: Read/Write  
  
 The number of times for the local system to poll the remote system, if there is no response.  
  
 **SdlcPollTO**  
 Data Type: **sint16** Qualifiers: **MINVALUE(1), MAXVALUE(300)** Access Type: Read/Write  
  
 The length of time, in tenths of a second, for the local system to wait for a response to a poll before trying again.  
  
 **SdlcPollRate**  
 Data Type: **sint16** Qualifiers: **MINVALUE(1), MAXVALUE(50)** Access Type: Read/Write  
  
 The poll rate, in polls per second. Valid only if the remote system is a peer or downstream system.  
  
 **SdlcStandby**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to set the Standby line to of a modem; otherwise, **false**.  
  
 **SdlcSwitchTO**  
 Data Type: **sint16** Qualifiers: **MINVALUE(10), MAXVALUE(500)** Access Type: Read/Write  
  
 The number of seconds that are allowed for the user or modem to dial and make a connection to the remote computer.  
  
 **MaxBtu**  
 Data Type: **sint32** Qualifiers: **MINVALUE(265), MAXVALUE(16393)** Access Type: Read/Write  
  
 The Maximum Basic Transmission Unit (BTU) length.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
