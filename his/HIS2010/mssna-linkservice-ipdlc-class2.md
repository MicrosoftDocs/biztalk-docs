---
title: "MsSna_LinkService_IpDlc Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ac22b4c-11a4-431f-ad1c-48acb1595862
caps.latest.revision: 5
---
# MsSna_LinkService_IpDlc Class
The **MsSna_LinkService_IpDlc** class represents the SNA IP-DLC link service.  
  
 The following syntax is simplified from MOF code and includes all inherited properties. For reference information about methods, see the table of methods later in this topic.  
  
## Syntax  
  
```  
  
Class MsSna_LinkService_IpDlc : MsSNA_LinkService  
{  
   String Name;  
   String DllName;  
   Boolean IsRemotable;  
   String Title;  
   String DriverName;  
   uint32 Type;  
   String PrimaryNNS;  
   String BackupNNS;  
   uint32 AddressType;  
   String LocalAddress;  
   String NetworkName;  
   String CPName;  
   String NodeID;  
   String LENNode;  
   String ResolvedIP;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key**, **MaxLen(8)** Access Type: Read-Only  
  
 A US_ASCII string containing the name of the link service. The name will be assigned automatically for a new link service.  
  
 **DllName**  
 Data Type: **String**Access Type: Read-Only  
  
 The name of the .dll that implements the link service.  
  
 **IsRemotable**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** if the link service can be used from a remote node; otherwise, **false**. **IsRemotable** is always **false** for the IP-DLC link service.  
  
 **Title**  
 Data Type: **String**Qualifiers: **MaxLen(255)** Access Type: Read/Write  
  
 The title of the link service, up to 128 symbols long.  
  
 **DriverName**  
 Data Type: **String** Access Type: Read-Only  
  
 The device driver associated with the link service. **DriverName** is used for the IP-DLC link service.  
  
 **Type**  
 Data Type: **uint32** Access Type: Read-Only  
  
 The type of link service. The following table describes the possible values for **Type**.  
  
|Value|Meaning|  
|-----------|-------------|  
|3|SDLC|  
|4|X25|  
|10|DFT|  
|11|DLC8022|  
|31|TWINAX|  
|32|CHANNEL|  
|35|IPDLC|  
  
 As an IP-DLC link service, **MsSna_LinkService_IpDlc.Type** will always be set to 35.  
  
 **PrimaryNNS**  
 Data Type: **String** Qualifiers: **MaxLen(128)** Access Type: Read/Write  
  
 Contains the name of the primary NNS server.  
  
 **BackupNNS**  
 Data Type: **String** Qualifiers: **MaxLen(1024)** Access Type: Read-Only  
  
 Contains the list of backup NNS delimited with semicolons. While **BackupNNS** may contain additional names, the current build is tested only for **BackupNNS** to be equal to the **PrimaryNNS**.  
  
 **AddressType**  
 Data Type: uint32 Access Type: Read/Write  
  
 Describes the local address type. The following table describes the possible values of **AddressType**.  
  
|Value|Description|  
|-----------|-----------------|  
|1|ADAPTER|  
|2|STATICIP|  
  
 **LocalAddress**  
 Data Type: **String** Qualifiers: **MaxLen(256)** Access Type: Read/Write  
  
 Contains the local network adapter or address. If **AddressType** contains a 1, **LocalAddress** will contain a valid network adapter; otherwise, **LocalAddress** contains a static IP address.  
  
 **NetworkName**  
 Data Type: **String** Qualifiers: **MaxLen(8)**, **ToUpperCase** Access Type: Read/Write  
  
 The network name of the Branch Network Node as implemented by the link service. The string will be a Type A string containing up to eight symbols.  
  
 **CPName**  
 Data Type: **String** Qualifiers: **MaxLen(8)**, **ToUpperCase** Access Type: Read/Write  
  
 Control point name of the Branch Network Node as implemented by the link service. The string will be a Type A string containing up to eight symbols.  
  
 **NodeID**  
 Data Type: **String** Qualifiers: **MaxLen(9)** Access Type: Read/Write  
  
 The identity of the Branch Network Node as implemented by the link service. **NodeID** will be in format HHH.HHHHH, where H is a hexadecimal digit.  
  
 **LENNode**  
 Data Type: **String** Qualifiers: **MaxLen(20)** Access Type: Read/Write  
  
 The name of the Associated LEN node.  
  
 **ResolvedIP**  
 Data Type: **String** Access Type: Read-only  
  
 The resolved IP address of the network adapter or local address.  
  
## Methods  
 The following table describes the methods implemented for the **MsSna_LinkService_IpDlc** class.  
  
|Method|Description|  
|------------|-----------------|  
|[GetAllStaticIPs](../HIS2010/mssna-linkservice-ipdlc-getallstaticips-method2.md)|Returns the list of all the static IP addresses on the local machine.|  
|[GetAllNetworkAdapters](../HIS2010/mssna-linkservice-ipdlc-getallnetworkadapters-method2.md)|Returns the list of all network adapters with the IP protocols enabled.|  
|[GetNextAvailableOrdinal](../HIS2010/mssna-linkservice-ipdlc-getnextavailableordinal-method1.md)|Internal. Provides the next available link service number.|  
  
## Requirements  
 Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaLinkServiceMS WMI Provider Classes](../HIS2010/wmisnalinkservicems-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](../HIS2010/administration-and-management-programmer-s-guide1.md)