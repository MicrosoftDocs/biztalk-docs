---
title: "MSBTS_HostInstance.Install Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5859491c-44fb-4cee-945f-a0ef53be1866
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.Install Method
Installs a service for the given instance of the BizTalk host.  
  
## Method Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 Install(string Logon, string Password, boolean GrantLogOnAsService);  
```  
  
## Parameters  
 *Logon*  
 String containing the logon information used by the host instance.  
  
 *Password*  
 String containing the password for the host.  
  
 *GrantLogOnAsService*  
 Boolean determining whether the 'Log On As Service' privilege should be automatically granted to the specified logon user or not. This flag only has effect when the [HostType](../core/msbts-hostinstance-hosttype-property-wmi.md) property is set to In-process.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.