---
description: "Learn more about: MsHisTrace_Event Class"
title: "MsHisTrace_Event Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../core/wmisnatrace-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
