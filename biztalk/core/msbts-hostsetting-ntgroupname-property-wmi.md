---
title: "MSBTS_HostSetting.NTGroupName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e18ead8-6eef-4627-b75b-4d59748d247d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.NTGroupName Property (WMI)
Contains the name of the Windows NT group.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string NTGroupName;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 The Windows NT group can be either a local or a domain Windows NT group. The group is granted access to the application queue created for the application type. The account used to host the application instances must be a member of the group.  
  
 The maximum length for this property is 63 characters.  
  
 For sample code using the **MSBTS_HostSetting** class, see [Creating, Updating, and Deleting a Host Instance Using WMI](../core/creating-updating-and-deleting-a-host-instance-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.