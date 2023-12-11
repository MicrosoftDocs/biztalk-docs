---
description: "Learn more about: MsSna_Domain Class"
title: "MsSna_Domain Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MsSna_Domain Class
Contains global properties that affect all servers in the group.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_Domain : MsSna_Config  
{  
   String Name;  
   String NetViewConnection;  
   String DispVerbConnection;  
   String EventlogServer;  
   String PopupServer;  
   sint16 AuditLevel;  
   sint32 BroadcastMeanTime;  
   boolean NamedPipes;  
   boolean IpxSpx;  
   boolean BanyanVines;  
   boolean TcpIp;  
   boolean RTMOverflow;  
   boolean RTMEndOfSession;  
   sint16 RTMTimerUntil;  
   sint16 RTMThreshold1;  
   sint16 RTMThreshold2;  
   sint16 RTMThreshold3;  
   sint16 RTMThreshold4;  
   String ConfigServer;  
   String ClientBackupSponsorNames;   // names separated by ';'  
   String ClientBackupDomainName;  
   sint16 ClientDomainBackupType;  
   boolean Security3270;  
   boolean SecurityLUA;  
   boolean SecurityAPPC;  
   sint32 Status;  
   datetime DateTimeSaved;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**  
  
 Qualifiers: **Key**  
  
 Access Type: Read-Only  
  
 The name of the subdomain.  
  
 **NetViewConnection**  
 Data Type: **String**  
  
 Qualifiers: **MAXLEN(8)**  
  
 Access Type: Read/Write  
  
 A connection to which NetView data should be sent.  
  
 **DispVerbConnection**  
 Data Type: **String**  
  
 Qualifiers: **MAXLEN(8)**  
  
 Access Type: Read/Write  
  
 The default connection for Display verbs. If set to **null**, selects a random connection.  
  
 **EventlogServer**  
 Data Type: **String**  
  
 Qualifiers: **MAXLEN(16)**  
  
 Access Type: Read/Write  
  
 The name of the server on which Windows Event Logs for this server installation should be stored.  
  
 **PopupServer**  
 Data Type: **String**  
  
 Qualifiers: MAXLEN(16)  
  
 Access Type: Read/Write  
  
 The name of the server to which pop-up error messages should be routed.  
  
 **AuditLevel**  
 Data Type: **sint16**  
  
 Qualifiers: **QualifierType**  
  
 Access Type: Read/Write  
  
 The default audit log level, which determines what events, if any, are audited. The following table describes the possible values for **AuditLevel**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Detailed|  
|1|General|  
|2|Significant|  
|3|Disabled|  
  
 **BroadcastMeanTime**  
 Data Type: **sint32**  
  
 Qualifiers: **MINVALUE(45), MAXVALUE(65535), UNITS("sec")** Access Type: Read/Write  
  
 The interval at which server broadcasts are repeated.  
  
 **NamedPipes**  
 Data Type: **Boolean**  
  
 Access Type: Read/Write  
  
 **true** to send server broadcasts over Windows Networking, also known as named pipes; otherwise, **false**.  
  
 **TcpIp**  
 Data Type: **Boolean**  
  
 Access Type: Read/Write  
  
 **true** to send server broadcasts over TCP/IP; otherwise, **false**.  
  
 **RTMOverflow**  
 Data Type: **Boolean**  
  
 Access Type: Read/Write  
  
 **true** to cause Response Time Monitor (RTM) data to be sent to the host when the number of host responses in a given time period overflows the size of the available counter; otherwise, **false**.  
  
 **RTMEndOfSession**  
 Data Type: **Boolean**  
  
 Qualifiers: **QualifierType**  
  
 Access Type: Read-Only  
  
 **true** to cause Response Time Monitor (RTM) data to be sent to the host at the end of each LU-to-LU session; otherwise, **false**.  
  
 **RTMTimerUntil**  
 Data Type: **sint16**  
  
 Access Type: Read-Only  
  
 The point at which the Response Time Monitor (RTM) registers that a host has responded, at which point the RTM stops the timers. The following table describes the possible values for **RTMTimerUnit**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|FirstData|  
|1|Unlock|  
|2|AllowSent|  
  
 **RTMThreshold1**  
 Data Type: **sint16**  
  
 Qualifiers: **MINVALUE(1), MAXVALUE(1000), UNITS("tenthsec")**  
  
 Access Type: Read/Write  
  
 The cut-off times at which the RTM saves the count of host responses, and then restarts the count.  
  
 **RTMThreshold2**  
 Data Type: **sint16**  
  
 Qualifiers: **MINVALUE(1), MAXVALUE(1000), UNITS("tenthsec")**  
  
 Access Type: Read/Write  
  
 The cut-off times at which the RTM saves the count of host responses, and then restarts the count.  
  
 **RTMThreshold3**  
 Data Type: **sint16**  
  
 Qualifiers: **MINVALUE(1), MAXVALUE(1000), UNITS("tenthsec")**  
  
 Access Type: Read/Write  
  
 The cut-off times at which the RTM saves the count of host responses, and then restarts the count.  
  
 **RTMThreshold4**  
 Data Type: **sint16**  
  
 Qualifiers: **MINVALUE(1), MAXVALUE(1000), UNITS("tenthsec")**  
  
 Access Type: Read/Write  
  
 The cut-off times at which the RTM saves the count of host responses, and then restarts the count.  
  
 **ConfigServer**  
 Data Type: **sint16**  
  
 Qualifiers: **MAXLEN(16)**  
  
 Access Type: Read/Write  
  
 The primary configuration server for the subdomain.  
  
 **ClientBackupSponsorNames**  
 Data Type: **String**  
  
 Qualifiers: **MAXLEN(256)**  
  
 Access Type: Read/Write  
  
 A list describing all of the SNA sponsor servers to which the server updates the client. The names of each server must be separated with a semicolon (;).  
  
 **ClientBackupDomainName**  
 Data Type: **String**  
  
 Qualifies: **MAXLEN(16)**  
  
 Access Type: Read/Write  
  
 A list of backup SNA subdomains with which the server updates the client.  
  
 **ClientDomainBackupType**  
 Data Type: **sint16**  
  
 Access Type: Read/Write  
  
 A value describing how client backup information is sent. The following table describes the possible values for **ClientDomainBackupType**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|None|  
|1|Domain|  
|2|Sponsors|  
  
 **Security3270**  
 Data Type: **Boolean**  
  
 Access Type: Read/Write  
  
 **true** if access to 3270 LUs is restricted to users assigned to the LU; otherwise, **false**.  
  
 **SecurityLUA**  
 Data Type: **Boolean**  
  
 Access Type: Read/Write  
  
 **true** if access to LUA LUs is restricted to users assigned to the LU; otherwise, **false**.  
  
 **SecurityAPPC**  
 Data Type: **Boolean**  
  
 Access Type: Read/Write  
  
 **true** if access to APPC LUs is restricted to users assigned to the LU; otherwise, **false**.  
  
 **Status**  
 Data Type: **sint32**  
  
 Access Type: Read-Only  
  
 The status of the subdomain.  
  
 **DateTimeSaved**  
 Data Type: **datetime**  
  
 Access Type: Read-Only  
  
 The time and date for which the object was saved.  
  
## Remarks  
 The object **MsSna_Domain** represents can also be referred to as a subdomain or OU.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11 and Windows 10  
  
## See Also  
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
