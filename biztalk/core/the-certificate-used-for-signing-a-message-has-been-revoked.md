---
description: "Learn more about: The certificate used for signing a message has been revoked"
title: "The certificate used for signing a message has been revoked"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The certificate used for signing a message has been revoked
## Details  
  
| Field | Error Details|
|-----------------|------------------------------------------------------------------------------------------|
|  Product Name   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]    |
| Product Version |                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                |
|    Event ID     |                                            -                                             |
|  Event Source   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI  |
|    Component    |                                        AS2 Engine                                        |
|  Symbolic Name  |                          SigningCertificateHasBeenRevokedError                           |
|  Message Text   | The certificate used for signing a message has been revoked. Certificate thumbprint: {0} |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the certificate identified as the signing certificate has been revoked.  
  
## User Action  
 To resolve this error, do one of the following:  
  
-   Create a new certificate to replaced the revoked certificate. Add the certificate to the Current User certificate store, identify it as the signing certificate in the Certificate page of the Group Properties dialog box, and then send the public key of the certificate to the recipient of the AS2 message.  
  
-   Disable the revocation list check by opening the BizTalk Server Administration Console, opening the AS2 Properties dialog box for the party resolved for the outgoing message, clicking the General node, and then clearing the Check Certification Revocation List property.
