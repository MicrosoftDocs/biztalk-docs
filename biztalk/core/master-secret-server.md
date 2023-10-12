---
description: "Learn more about: Master Secret Server"
title: "Master Secret Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Master Secret Server
The master secret server is the Enterprise Single Sign-On (SSO) server that stores the master secret (encryption key). The master secret server generates the master secret when an SSO administrator requests it. The master secret server stores the encrypted master secret in the registry. Only Single Sign-On administrators can access the master secret.  
  
 The other Single Sign-On servers check every 30 seconds to see whether the master secret has changed. If it has changed, they read it securely; otherwise, they continue to use the master secret they already have cached in memory. The SSO service uses the master secret to encrypt and decrypt the user credentials.  
  
 You cannot use the SSO system until an SSO administrator configures the master secret server and generates the master secret. The master secret server generates the master secret during configuration. Only SSO administrators can generate the master secret. An SSO administrator must configure the master secret server and the SSO database before an application can use the SSO service.  
  
> [!IMPORTANT]
>  After you generate the master secret, it is strongly recommended that you back it up and store it in a secure location.  
  
 When an SSO administrator needs to regenerate the master secret, for example, if the SSO administrator wants to change the master secret periodically, the master secret server stores both the old and new master secret. The master secret server then goes through all the mappings, decrypts them using the old master secret, and encrypts them again using the new master secret.  
  
 If the master secret server fails, all runtime operations already running will continue to run, but SSO servers will not be able to encrypt new credentials.  
  
> [!IMPORTANT]
>  There can be only one master secret server in your SSO system. Therefore, it is strongly recommended you cluster the master secret server. For more information, see [How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md).  
  
## See Also  
 [Using SSO](../core/using-sso.md)
