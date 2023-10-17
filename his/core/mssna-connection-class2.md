---
description: "Learn more about: MsSna_Connection Class"
title: "MsSna_Connection Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSna_Connection Class
Base class for SNA connection.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_Connection : MsSna_Config  
{  
   String Service;  
   String Name;  
   String Comment;  
   String Adapter;  
   sint32 RemoteEnd;  
   sint16 PeerRole;  
   sint16 Activation;  
   boolean AllowIncoming;  
   boolean DynamicLuDef;  
   String PartnerConnectionName;  
   String BlockId;  
   String NodeId;  
   String RemoteNetName;  
   String RemoteControlPoint;  
   String RemoteBlockId;  
   String RemoteNodeId;  
   sint16 XIDFormat;  
   String LocalNetName;  
   String LocalControlPoint;  
   sint16 CompressionLevel;  
   sint16 RetryLimit;  
   sint16 RetryDelay;  
   String StatusText;  
}  
```  
  
## Properties  
 **Service**  
 Data Type: **String** Qualifiers: **MAXLEN(20)** Access Type: Read-Only  
  
 The SNA service to which this connection belongs.  
  
 **Name**  
 Data Type: **String** Qualifiers: **Key, MAXLEN(8)** Access Type: Read-ONly  
  
 The connection name.  
  
 **Comment**  
 Data Type: **String** Qualifiers: **MAXLEN(25)** Access Type: Read/Write  
  
 An optional comment field.  
  
 **Adapter**  
 Data Type: **String** Qualifiers: **MAXLEN(8)** Access Type: Read/Write  
  
 The link service to be used by this connection.  
  
 **RemoteEnd**  
 Data Type: **sint32** Access Type: Read/Write  
  
 The remote end. The following table describes the possible values of **RemoteEnd**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Host|  
|1|Peer|  
|2|Downstream|  
|3|Passthrough|  
  
 For 3270 or LUA access, be sure to set **RemoteEnd** to *Host*.  
  
 **PeerRole**  
 Data Type: **String** Access Type: Read/Write  
  
 The peer role. The following table describes the possible values of **PeerRole**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Primary|  
|1|Secondary|  
|2|Negotiable|  
|-1|Invalid|  
  
 **PeerRole** only applies to connections with **RemoteEnd** set to **Peer** or **Passthrough**.  
  
 **Activation**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The activation setting. Applicable only if Outgoing Calls are included in Allowed Directions. The following table describes the possible values for **Activation**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Initial|  
|1|OnDemand|  
|2|Administrator|  
|3|Incoming|  
  
 **AllowIncoming**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to indicate that incoming calls are allowed; otherwise, **false**.  
  
 **DynamicLuDef**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to automatically configure the APPC Remote LUs as users request them; otherwise, **false**. **DynamicLuDef** requires that an APPN End Node or Net Node be available on the connection.  
  
 **PartnerConnectionName**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The name of the connecting partner. Valid only if **RemoteEnd** is of **Passthrough**.  
  
 **BlockId**  
 Data Type: **String** Qualifiers: **MAXLEN(3), TOUPPERCASE** Access Type: Read/Write  
  
 The block ID.  
  
 **NodeId**  
 Data Type: **String** Qualifiers: **MAXLEN(5), TOUPPERCASE** Access Type: Read/Write  
  
 The local node ID. Applicable only for connections which use a switched SDLC line (standard telephone line) to connect to a host system.  
  
 **RemoteNetName**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The network name of the remote system. Applicable if you are using Format 3 XIDs.  
  
 **RemoteControlPoint**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The control point of the reomote system. Applicable if you are using Format 3 XIDs.  
  
 **RemoteBlockId**  
 Data Type: **String** Qualifiers: **MAXLEN(3), TOUPPERCASE** Access Type: Read/Write  
  
 The remote block ID.  
  
 **RemoteNodeId**  
 Data Type: **String** Qualifiers: **MAXLEN(5), TOUPPERCASE** Access Type: Read/Write  
  
 The remote node ID.  
  
 **XIDFormat**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The XID Type. The following table describes the possible values for **XIDFormat**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Format 0|  
|3|Format 3|  
  
 Most systems use Format 3.  
  
 **LocalNetName**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The network name that, along with the **LocalControlPoint**, identifies a system.  
  
 **LocalControlPoint**  
 Data Type: **String** Qualifiers: **MAXLEN(8), TOUPPERCASE** Access Type: Read/Write  
  
 The control point that, along with **LocalNetName**, identifies a system.  
  
 **CompressionLevel**  
 Data Type: **sint16** Access Type: Read/Write  
  
 The compression type used by this connection. The following table describes the possible values for **CompressionLevel**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|None|  
|1|RLE|  
|2|LZ9|  
|3|LZ10|  
|4|LZ12|  
  
 **RetryLimit**  
 Data Type: **sint16** Qualifiers: **MINVALUE(0), MAXVALUE(255)** Access Type: Read/Write  
  
 The number of times the local system tries to send data to the remote system if there is no response.  
  
 **RetryDelay**  
 Data Type: **String** Qualifiers: **MINVALUE(0), MAXVALUE(255), UNITS("sec")** Access Type: Read/Write  
  
 The length of time for the local system to wait for a response to a transmission before trying again.  
  
 **StatusText**  
 Data Type: **String** Access Type: Read-Only  
  
 The current status of the connection. The following table describes the possible values of **StatusText**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Unconfigured|  
|1|Inactive|  
|2|Incoming|  
|3|OnDemand|  
|4|OnDemand/Incoming|  
|5|Pending|  
|6|Stopping|  
|7|Active|  
|8|Error|  
|9||  
  
 **Name**  
 Data Type: **String** Qualifiers: **Something** Access Type: Read/Write  
  
 The name of the connection.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|[Start](../core/mssna-connection-start-method1.md)|Starts the connection.|  
|[Stop](../core/mssna-connection-stop-method1.md)|Stops the connection.|  
|[ExchangePassthroughLus](../core/mssna-connection-exchangepassthroughlus-method2.md)|Returns a value that determines if two LUs are part of a passthrough connection pair.|  
  
## Remarks  
 **MsSna_Connection** belongs to a SNA service, and may own 3270 LUs.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
