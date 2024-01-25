---
description: "Learn more about: Encryption and Signing Certificates"
title: "Encryption and Signing Certificates"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Encryption and Signing Certificates
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] relies heavily on the security provided by certificates. By using certificates for encryption and digital signatures, BizTalk Server can send and receive data that can be trusted, and can help ensure that the data it processes is secure. For both encryption and digital signatures, there is a public key certificate and a private key certificate. For encryption, the sender of the message uses the receiver's public key certificate to encrypt the message, while the receiver of the message (BizTalk Server) uses its private key to decrypt the message. For digital signatures, the sender of the message uses a private key certificate to sign the message, and the receiver of the message (BizTalk Server) uses the public key certificate of the sender to verify the signature.

 BizTalk Server uses public key certificates to verify the digital signatures of inbound messages and for encrypting outbound messages. BizTalk Server uses private key certificates for decrypting inbound messages and signing outbound messages.

 You configure the certificates BizTalk Server uses in BizTalk Explorer and in the BizTalk Administration Console.

 For more information about digital certificates, see [Certificates that BizTalk Server Uses for Signed Messages](/biztalk/core/certificates-that-biztalk-server-uses-for-signed-messages).

> [!NOTE]
> To make sure that a certificate hasn't expired and that the certificate is trusted down to a Root Certificate Authority (CA), you can choose to have the BizTalk Server engine check the Certificate Revocation List (CRL) while the engine processes Secure Multipurpose Internet Mail Extensions (S/MIME) messages. This verification occurs while the pipeline processes the message, in the MIME/SMIME decoder component. 
>
> For more information about how to set **Check Revocation List** property, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).

## In This Section

-   [Certificate Stores that BizTalk Server Uses](../core/certificate-stores-that-biztalk-server-uses.md)

-   [Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)

-   [Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)
