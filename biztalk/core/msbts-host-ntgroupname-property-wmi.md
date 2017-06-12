---
title: "MSBTS_Host.NTGroupName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a04332fa-cc65-4bc0-b8fb-6ee10b25d8ef
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host.NTGroupName Property (WMI)
Contains the name of the Microsoft Windows NT group.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string NTGroupName;  
```  
  
## Remarks  
 In each database, BizTalk Server creates a SQL role for this host Windows user group and grants this role the minimum user rights it needs for the user group to perform tasks for this host. Unless your BizTalk system is a single box system (a single BizTalk server and SQL server is on the same local machine), it is highly recommended that a Windows domain user group (instead of a local user group) be specified for this property. Otherwise, if local user group is specified, you must ensure that this local user group has been created on all of the SQL servers where BizTalk Server databases reside in order for BizTalk Server to grant database access to this group.  
  
 This property is read-only.  
  
 The maximum length for this property is 63 characters.  
  
 For more information about accounts in BizTalk Server, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.