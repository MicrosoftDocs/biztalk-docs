---
title: "MSBTS_HostInstance.NTGroupName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e54d0e9-ced7-4884-89ec-bbc96b8a77d9
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.NTGroupName Property (WMI)
Contains the name of the Microsoft Windows NT group.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string NTGroupName;  
```  
  
## Remarks  
 This property is read only.  
  
 The Windows NT group can be either a local or a domain Windows NT group. The group is granted access to the application queue created for the host type. The account used to host the host instances must be a member of the group. For more information about accounts in BizTalk Server, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
 The maximum length for this property is 63 characters.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.