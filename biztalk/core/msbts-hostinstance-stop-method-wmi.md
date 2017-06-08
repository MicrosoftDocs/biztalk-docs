---
title: "MSBTS_HostInstance.Stop Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4b7c69d-460c-4ebb-869b-0dfe698494ba
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.Stop Method (WMI)
Stops the given instance of the BizTalk host.  
  
## Method Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 StopService();  
```  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 For more information about the minimum security user rights required to administer a Host instance, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
> [!NOTE]
>  Always specify the name of the local server when using WMI. When you enumerate host instances, both local and remote instances will be returned. You can then call the start or stop methods.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.