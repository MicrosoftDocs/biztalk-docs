---
title: "SSO with Host-Initiated Processing1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 784dfb05-96ab-49b7-90cb-94c1795b0cf5
caps.latest.revision: 4
---
# SSO with Host-Initiated Processing
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
 [Mainframe Authentication for CICS LINK &#91;HIS2010&#93; &#91;Duplicate&#93;](http://msdn.microsoft.com/en-us/4fef4fca-42b5-4453-94aa-11e0258c3ffc)   
 [AS/400 Security &#91;HIS2010&#93; &#91;Duplicate&#93;](http://msdn.microsoft.com/en-us/dc45d5d8-e78f-4b9e-afbb-443d2abec1c2)   
 [Limitations of User Access Level Sign On &#91;HIS2010&#93; &#91;Duplicate&#93;](http://msdn.microsoft.com/en-us/a58d5f4c-5856-40a7-a71d-4699c5773c84)   
 [SSO with Encrypted Passwords](../core/sso-with-encrypted-passwords.md)   
 [Threat Mitigation within Visual Studio &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/16f1392e-f1e6-44f7-9db7-213625c38897)   
 [Application Integration Security Guide &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/6f9e1a23-1988-4d43-a7d6-9444efc31dd3)