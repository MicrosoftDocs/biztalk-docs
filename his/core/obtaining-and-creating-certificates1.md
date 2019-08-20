---
title: "Obtaining and Creating Certificates1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c660a45-e2ee-4b4c-a941-b829baa0f7d6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Obtaining and Creating Certificates
It is recommended that you use the Microsoft Certificate Services and certification authorities to manage certificates.  
  
 When a certificate is issued, it includes a certificate and a private key. When the certificate is transmitted for verification purposes, only the certificate part is sent (and not the private key). The server needs a certificate and a private key for the server authentication certificate. The server needs a copy of the client authentication certificate for its root CA.  
  
## Obtaining Certificates  
 Certificates are obtained from certification authorities. Because these CAs are widely trusted organizations, the certificate will be recognized widely.  
  
## Creating Certificates  
 Windows Server features a certification authority program that allows a local CA to be set up. The local CA may depend on a certificate obtained from an external, well-trusted CA, or it may be a stand-alone CA.  
  
 This system can be used if the root certificate (on the CA program) is copied to the Trusted Root CAs store on all the computers using the certificates. The local CA can then issue client and server authentication certificates, and each will be recognized by the other.  
  
## See Also  
 [Server Authentication](../core/server-authentication1.md)   
 [Client Authentication](../core/client-authentication2.md)