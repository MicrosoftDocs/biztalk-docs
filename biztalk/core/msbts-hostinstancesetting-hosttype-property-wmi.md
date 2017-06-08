---
title: "MSBTS_HostInstanceSetting.HostType Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d412cdc-458c-493a-a85e-31c6b1596034
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstanceSetting.HostType Property (WMI)
Indicates which runtime model the instances of the BizTalk Host will be running in.  
  
> [!NOTE]
>  The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
uint32 HostType;  
```  
  
## Remarks  
 This property is read-only.  
  
 The following table contains the permissible values for this property:  
  
|Description|Value|  
|-----------------|-----------|  
|In-process|1|  
|Isolated|2|  
  
 Note that the integer values must be used in code and script.  
  
## Requirements  
 **Header**: Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace**: Included in \root\MicrosoftBizTalkServer.