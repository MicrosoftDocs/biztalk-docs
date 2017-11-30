---
title: "SSO with Encrypted Passwords1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efea1d1e-5e17-4198-9ec2-bdec46401f53
caps.latest.revision: 5
---
# SSO with Encrypted Passwords
If you are using Single Sign-On (SSO) security, you must determine whether the client application passes plain text passwords or encrypted passwords to the Transaction Integrator (TI) run-time environment. If the passwords are in plain text, SSO accepts the passwords when they are submitted by the TI run-time environment. If the passwords are encrypted, SSO does not accept the passwords, and the call to SSO fails. To avoid failed SSO calls, disable password validation for the SSO affiliate application.  
  
## See Also  
 [Transaction Integrator Security &#91;bpi&#93; &#91;HIS09_R2&#93;](http://msdn.microsoft.com/en-us/33cffca2-df3f-4856-9725-f8c35b97c1c6)