---
title: "Server Authentication1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94ae37a9-9d9a-4ac9-84b9-99932d47dd8e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Server Authentication
For server authentication, the server requires a valid certificate with the following properties:  
  
- Type X509  
  
- Suitable for Server Authentication  
  
- Associated private key  
  
- Stored in the Personal or My certificate store for the service account used by the TN3270 service  
  
- By default, a TN3270 server will look for a certificate with a Common Name (CN) matching the host name of the computer running the TN3270 server. This default can be changed by using a registry entry. For details, see [Changing the Default Server Authentication Certificate Common Name (CN)](../core/changing-the-default-server-authentication-certificate-common-name-cn-2.md).  
  
  This certificate will be sent to the client as part of the handshake negotiation when the connection is established. For the client to accept the certificate:  
  
- The certificate (and its issuing chain) must be current (for example, not outside of its valid dates).  
  
- The issuing chain must lead to a certification authority (CA) that appears in the clients Trusted Root CA List.  
  
- The certificate (or any part of its issuing chain) should not appear on a certificate revocation list (CRL) of its issuer.  
  
- Most clients offer strict certificate checking, which if selected, will reject connections if the server certificates common name does not match its host name.  
  
> [!NOTE]
>  If the certificate on the server is changed, the TN3270 server must be stopped and restarted.  
  
## See Also  
 [Client Authentication](../core/client-authentication2.md)   
 [Obtaining and Creating Certificates](../core/obtaining-and-creating-certificates1.md)