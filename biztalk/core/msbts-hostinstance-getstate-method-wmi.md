---
title: "MSBTS_HostInstance.GetState Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc8502b8-50db-47fe-b403-57a258be45f5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.GetState Method (WMI)
Retrieves the state of the given instance of the BizTalk host.  
  
## Method Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 GetState(   
          [out] uint32 State  
);  
```  
  
## Parameters  
 *State*  
  
 [out] **Integer** describing the state of the BizTalk host instance.  
  
## Remarks  
 The following table contains the possible values for the *State* parameter:  
  
|Description|Value|  
|-----------------|-----------|  
|Stopped|1|  
|Start pending|2|  
|Stop pending|3|  
|Running|4|  
|Unknown|8|  
  
 Note that the integer values must be used in code and script.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.