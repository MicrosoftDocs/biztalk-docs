---
title: "SSO with Host-Initiated Processing | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 784dfb05-96ab-49b7-90cb-94c1795b0cf5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO with Host-Initiated Processing

## Overview
When you use Single Sign-On (SSO) security with host-initiated processing (HIP), the impersonation of user credentials is handled differently depending upon whether you are calling a .NET object or a COM object. If HIP is calling a .NET object, there are no special considerations; the Transaction Integrator (TI) run-time environment impersonates the user account. If HIP is calling a COM object, however, there are special considerations.  
  
 Depending on the threading model and registration type of the components, the following actions occur when HIP calls the method of a .COM object when it is impersonating a user account (the one that the host credentials would have been mapped to via SSO):  
  
|Threading Model|Registration|Actions|  
|---------------------|------------------|-------------|  
|Single, apartment|Server/Library/No COM+ application|-   Server object methods are called under HIP Service/COM+ application configured identity.<br />-   Server object methods call **CoImpersonateClient** to start impersonating the user identity.<br />-   Optionally, methods can call **CoRevertToSelf**, although that is not necessary because COM will call it anyway after the method returns.|  
|Free, both, neutral|Server COM+ application|-   Server object methods are called under HIP Service/COM+ application configured identity.<br />-   Server object methods call **CoImpersonateClient** to start impersonating the user identity.<br />-   Optionally, methods can call **CoRevertToSelf**, although that is not necessary because COM will call it anyway after the method returns.|  
|Free, both, neutral|Library/No COM+ application|-   Server object methods are called under the user identity being impersonated.<br />-   Server object method should not call **CoImpersonateClient** or **CoRevertToSelf** because they would fail with RPC_E_CALL_COMPLETE.|  
  
 If you are programming in Microsoft Visual Basic® 6.0, be sure to include the **CoImpersonateClient** and **CoRevertToSelf** declarations in your programs:  
  
```  
Private Declare Function CoImpersonateClient Lib "ole32.dll" () As Long  
Private Declare Function CoRevertToSelf Lib "ole32.dll" () As Long  
```  
  
## See Also  
 [SSO with Encrypted Passwords](../core/sso-with-encrypted-passwords2.md)   
