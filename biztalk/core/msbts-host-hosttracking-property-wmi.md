---
title: "MSBTS_Host.HostTracking Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32d3893f-a699-4ac4-99f6-e7ae08609a4e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host.HostTracking Property (WMI)
Indicates whether instances of this BizTalk Host will host the tracking sub service.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
boolean HostTracking;  
```  
  
## Remarks  
 This property is read-write.  
  
 At least one host in the group must host tracking. This option indicates whether the host loads the BizTalk Tracking component to process health monitoring and business data. Hosts that host tracking have read and write access to the tracking tables in the MessageBox database, as well as access to the tracking database. Therefore, any objects running in a host that hosts tracking also have access privileges to read and write to these database tables. Hosts that do not host tracking only have write access to the tracking tables in the MessageBox database, and no access to the tracking database.  
  
> [!NOTE]
>  Specifying a host to host tracking has an impact on the performance of BizTalk Server.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.