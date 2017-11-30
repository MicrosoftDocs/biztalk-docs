---
title: "Master Secret Server | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f605a62d-29b9-4465-be78-6554e9f11e5a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Master Secret Server
The *master secret server* is the Enterprise Single Sign-On (SSO) server that stores the master secret (encryption key). The master secret server generates the master secret when an SSO administrator requests it. The master secret server stores the encrypted master secret in the registry. Only Single Sign-On administrators can access the master secret.  
  
 The other Single Sign-On servers check every 30 seconds to see whether the master secret has changed. If it has changed, they read it securely; otherwise, they continue to use the master secret they already have cached in memory. The SSO service uses the master secret to encrypt and decrypt the user credentials.  
  
 You cannot use the SSO system until an SSO administrator configures the master secret server and generates the master secret. The master secret server generates the master secret during configuration. Only SSO administrators can generate the master secret. An SSO administrator must configure the master secret server and the Credential database before an application can use the SSO service.  
  
> [!IMPORTANT]
>  After you generate the master secret, it is strongly recommended that you back it up and store it in a secure location.  
  
 When an SSO administrator needs to regenerate the master secret, for example, if the SSO administrator wants to change the master secret periodically, the master secret server stores both the old and new master secret. The master secret server then goes through all the mappings, decrypts them using the old master secret, and encrypts them again using the new master secret.  
  
 If the master secret server fails, all runtime operations that are already running continue to run, but SSO servers are not able to encrypt new credentials.  
  
> [!IMPORTANT]
>  There can be only one master secret server in your SSO system. Therefore, it is strongly recommended you cluster the master secret server. For more information, see [How to Cluster the Master Secret Server](../esso/how-to-cluster-the-master-secret-server.md).  
  
## See Also  
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)   
 [Managing the Master Secret](../esso/managing-the-master-secret.md)