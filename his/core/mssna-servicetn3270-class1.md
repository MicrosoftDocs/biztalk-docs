---
title: "MsSna_ServiceTN3270 Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4824a0d-6b5d-4ad5-a690-4ebd7f160fdb
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# MsSna_ServiceTN3270 Class
Enables clients to connect to a host via the TN3270 protocol.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_ServiceTN3270 : MsSna_Service  
{  
   String Name;  
   String Comment;  
   boolean LogNormal;  
   boolean LogSna;  
   boolean UseNameResolution;  
   boolean PrinterFlowControl;  
   boolean TNModeOnly;  
   sint32 CloseDelay;  
   sint32 IdleTimeout;  
   sint32 InboundRU;  
   sint32 OutboundRU;  
   sint32 RefreshTime;  
   sint32 StatusDelay;  
      sint32 Port;  
   String StatusText;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: **MAXLEN(16)** Access Type: Read-Only  
  
 The TN3270 service name. **Name** is the same as the computer name.  
  
 **Comment**  
 Data Type: **String**Qualifiers: **MAXLEN(25)** Access Type: Read/Write  
  
 An optional comment string.  
  
 **LogNormal**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** if access to log successful client connections and successful client terminations; otherwise, **false**.  
  
 **LogSna**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to log all TN3270 service event messages to the Event Log being used by the Host Integration Server system, instead of to the Event Log on the local computer; otherwise, **false**.  
  
 **UseNameResolution**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to specify the name of a computer rather than the IP address—use only if you are running a domain name resolver; otherwise, **false**.  
  
 **PrinterFlowControl**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to have the TN3270 service send all messages to a TN3270 printer client as RESPONSE-REQUIRED, and not to send any messages until it has received a response for the previous message; otherwise, **false**.  
  
 **SocketListen**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 To have the TN3270 service stop listening on this socket once all of the defined LUs are in use; otherwise, **false**.  
  
 **TNModeOnly**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to prevent the TN3270 service from using TN3270E, an enhancement to TN3270; otherwise, **false**.  
  
 **CloseDelay**  
 Data Type: **sint32**Qualifiers: **MINVALUE(0), MAXVALUE(86400),UNITS("sec")** Access Type: Read/Write  
  
 The time between sending a disconnect message to the client computer and closing the socket with the client computer.  
  
 **IdleTimeout**  
 Data Type: **sint32**Qualifiers: **MINVALUE(0), MAXVALUE(70560),UNITS("min")** Access Type: Read/Write  
  
 The time in which the session idles before the TN3270 service disconnects the client system. Specifying 0 means there will be no time-out.  
  
 **InboundRU**  
 Data Type: **sint32**Qualifiers: **MINVALUE(256), MAXVALUE(32768),UNITS("bytes")** Access Type: Read/Write  
  
 The RU, or SNA message, size used by the TN3270 service for logon messages from the host.  
  
 **OutboundRU**  
 Data Type: **sint32**Qualifiers: **MINVALUE(256), MAXVALUE(32768),UNITS("bytes")** Access Type: Read/Write  
  
 The RU, or SNA message, size used by the TN3270 service for logon messages to the host.  
  
 **RefreshTime**  
 Data Type: **sint32**Qualifiers: **MINVALUE(0), MAXVALUE(60),UNITS("sec")** Access Type: Read/Write  
  
 The delay between updates of the status on the display.  
  
 **StatusDelay**  
 Data Type: **sint32**Qualifiers:MINVALUE<strong>(0), MAXVALUE(86400),UNITS("sec")</strong> Access Type: Read/Write  
  
 The delay between the time when TN3270 service connects to a host session and the time the TN3270 service starts updating the client screen.  
  
 **Port**  
 Data Type: **sint32**Qualifiers: <strong>MINVALUE(0), MAXVALUE(9999)</strong>Access Type: Read/Write  
  
 The default port number for the TN3270 service. You can override **Port** on a per-session basis. Use 0 for the default TN3270 port.  
  
 **StatusText**  
 Data Type: **String**Access Type: Read-Only  
  
 The current status of the service. The following table describes the possible values for **StatusText**.  
  
|Value|Description|  
|-----------|-----------------|  
|Not configured|The status is not configured.|  
|Inactive|The status is inactive.|  
|Pending|The status is pending.|  
|Stopping|The status is stopping.|  
|Active|The status is active.|  
|Out of Date|The status is out-of-date.|  
|Paused|The status is paused.|  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|**Start**|Starts the service.|  
|**Stop**|Stops the service.|  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)