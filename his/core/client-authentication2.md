---
description: "Learn more about: Client Authentication"
title: "Client Authentication2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Client Authentication
For client authentication, the client requires a valid certificate with the following properties:  
  
- Type X509  
  
- Suitable for Client Authentication  
  
- Associated private key  
  
  You might not want to grant access to some of these certificate settings. It is recommended that you check the list of default Trusted Root Certification Authorities on the server, and remove any you do not want.  
  
  How the certificate is stored and selected depends on the client program. The certificate will be passed to the server as part of the handshake process. For the server to accept the certificate:  
  
- The certificate (and its issuing chain) must be current.  
  
- The issuing chain must lead to a CA that appears in the servers Trusted Root CA list.  
  
- The certificate (or any part of its issuing chain) should not appear on a CRL of its issuer.  
  
## See Also  
 [Server Authentication](../core/server-authentication1.md)   
 [Obtaining and Creating Certificates](../core/obtaining-and-creating-certificates1.md)
