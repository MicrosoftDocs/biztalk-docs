---
title: "MsHisTrace_Event Class2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 498cfa09-f034-410a-b004-408ffad86066
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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
 **Platforms**: Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, Windows Server 2012  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../core/wmisnatrace-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)