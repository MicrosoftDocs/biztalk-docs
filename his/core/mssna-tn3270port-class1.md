---
title: "MsSna_TN3270Port Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 339f1aa3-4a72-4c58-8041-6630da1fa5c2
caps.latest.revision: 4
---
# MsSna_TN3270Port Class
Describes a port with security properties.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_TN3270Port : MsSna_Config  
{  
   String Service;  
   sint32 Port;  
   String Comment;  
   sint16 Security;  
   boolean ClientCertVal;  
   boolean Default;  
   String Name;  
};  
```  
  
## Properties  
 **Service**  
 Data Type: **String**Qualifiers: **Key, MAXLEN(20)**Access Type: Read/Write  
  
 The TN service to which this LU belongs.  
  
 **Port**  
 Data Type: **sint32**Qualifiers: **Key, MINVALUE(1), MAXVALUE(0xffff)** Access Type: Read/Write  
  
 The port number.  
  
 **Comment**  
 Data Type: **String**Qualifiers: **MAXLEN(25)**Access Type: Read/Write  
  
 An option comment field.  
  
 **Security**  
 Data Type: **sint16**Access Type: Read/Write  
  
 The security level. The following table describes the possible values for **Security**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Unsecured|  
|1|Low|  
|2|Medium|  
|3|High|  
  
 **ClientCertVal**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to indicate that the client ceritificate should be validated; otherwise, **false**.  
  
 **Default**  
 Data Type: **Boolean**Qualifiers: **(TRUE)**Access Type: Read-Only  
  
 **true** to indicate a default port; otherwise, **false**.  
  
 **Name**  
 Data Type: **String**Qualifiers: **Something**Access Type: Read/Write  
  
 Name of the port.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)