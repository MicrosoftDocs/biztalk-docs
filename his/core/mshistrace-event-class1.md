---
title: "MsHisTrace_Event Class1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6287bfaf-afd0-4b17-ac41-c9fb1c704102
caps.latest.revision: 4
---
# MsHisTrace_Event Class
The **MsHisTrace_Event** class retrieves error information.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHisTrace_Event : __ExtrinsicEvent  
{  
    string Name;  
    string PathToObj;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Access Type: Read/Write  
  
 Name of the event that occurred.  
  
 **PathToObj**  
 Data Type: **String** Access Type: Read/Write  
  
 Path to the object that describes the event.  
  
## Requirements  
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2008 R2  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../core/wmisnatrace-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](../core/administration-and-management-programmer-s-guide1.md)