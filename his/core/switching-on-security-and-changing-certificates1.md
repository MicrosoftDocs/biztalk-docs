---
title: "Switching on Security and Changing Certificates1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b837431f-de12-487b-88aa-1411d238b6bf
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Switching on Security and Changing Certificates
To support security, the TN server needs to load a server authentication certificate. This is done when a TN server receives a configuration requiring security (for example, at least one port is configured to a security level other than Unsecure) for the first time. After a certificate has been loaded successfully, the certificate cannot be changed without restarting the TN server.  
  
 If the certificate-loading process fails (for example, if the certificate is not found or is invalid), any ports requiring security will not be available to the TN server and an error will be logged. The user must then fix the certificate and try again.  
  
> [!NOTE]
>  The certificate-loading process incorporates several stages, such as opening a certificate store, finding the certificate, and acquiring credentials based on the certificate.  Obtaining credentials involves three steps:  
  
- Opening the servers certificate store (using **CertOpenStore**)  
  
- Obtaining the server authentication certificate (using **CertFindCertificateInStore**)  
  
- Getting a credential for each security setting (using **AcquireCredentialHandle**)  
  
  The credential contains all the security options supported by the credential (such as maximum and minimum encryption strength, and algorithms supported). Client authentication is not a credential property. The credential is linked to the server authentication certificate.  
  
  If security is specified but the TN3270 server fails to get the credentials, any ports that are defined as secure will be unavailable to clients. An error will be logged and the user can try to reload the credentials again.  
  
## See Also  
 [Configuring Certificates](../core/configuring-certificates2.md)   
 [Changing the Default Values of the Security Parameters](../core/changing-the-default-values-of-the-security-parameters1.md)   
 [Changing the Default Server Authentication Certificate Common Name (CN)](../core/changing-the-default-server-authentication-certificate-common-name-cn-2.md)