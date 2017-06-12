---
title: "MSBTS_Host.HostType Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dbeaabf-6a43-4b87-8f1e-cdf72481a418
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host.HostType Property (WMI)
Indicates which runtime model the instances of the BizTalk Host will be running in. The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
unint32 HostType;  
```  
  
## Remarks  
 This property is read only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|In-process|1|  
|Isolated|2|  
  
 In-process hosts represent service instances that an administrator creates, deletes, and fully controls with WMI and the BizTalk Administration console.  
  
 Isolated hosts represent service instances that a solutions developer programmatically creates, deletes, and controls. An administrator uses WMI and the BizTalk Administration console to configure these hosts (for example, to configure the host service account and authentication trust).  
  
 For more information about in-process and isolated hosts, see [Hosts](../core/hosts.md).  
  
 Note that the integer values must be used in code and script.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.