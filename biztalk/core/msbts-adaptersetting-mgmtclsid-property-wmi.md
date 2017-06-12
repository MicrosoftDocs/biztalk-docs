---
title: "MSBTS_AdapterSetting.MgmtCLSID Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a48c1bf-7ad8-4f23-a7b3-fac1d1a6146e
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_AdapterSetting.MgmtCLSID Property (WMI)
Gets the class identifier (CLSID) of the COM component responsible for managing this adapter.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string MgmtCLSID;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.