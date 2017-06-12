---
title: "MSBTS_AdapterSetting.Name Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43264ec1-652f-4c2f-b4a8-70f9f42fba13
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_AdapterSetting.Name Property (WMI)
Gets the name of the adapter.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string Name;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property has a **Key** qualifier. Along with [MgmtDbNameOverride](../core/msbts-adaptersetting-mgmtdbnameoverride-property-wmi.md) and [MgmtDbServerOverride](../core/msbts-adaptersetting-mgmtdbserveroverride-property-wmi.md), this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.