---
title: "InterAct Adapter Security Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4924b8c-1fda-4a0c-b9be-8f2ccba38013
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# InterAct Adapter Security Architecture
Security for the message transmission and receipt is implemented using the certificate and crypto features inherent in SWIFTNet Link (SNL) and the SWIFTAlliance Gateway (SAG). SWIFT recommends that services designed for InterAct to apply an “end-to-end” signature—that is, to sign both request and response messages.  
  
 The cryptographic operations are implemented by the security module of SWIFTNet Link. This module allows signature and encryption using PKI keys. The nature and extent of cryptography operations are specified as part of the Request and Response Control data structures passed to the APIs.  
  
 SWIFTNet supports the sign/encrypt of the RequestPayload or ResponsePayload. Also the RequestHeader or ResponseHeader can be signed.  
  
## Signing/Encrypting Requests and Responses  
 The rules for applying cryptographic operations on SWIFTNet InterAct Request elements are as follows:  
  
- RequestControl: this is destined to SWIFTNet only. SWIFTNet delivers a RequestDescriptor to the responder (and some elements also to the Requestor). Therefore, no client process to server process cryptographic operation can be performed on it.  
  
- RequestE2EControl: this element contains information to ensure reliable end-to-end messaging. No cryptographic operation can be performed on it.  
  
- RequestHeader: it is used by SWIFTNet and conveyed unchanged to the Responder. Therefore, this can only be signed.  
  
- RequestPayload: any cryptographic operations can be performed on this.  
  
- Crypto element(s): these relate to previously activated cryptographic operations on this Request. No cryptographic operations can be performed on these.  
  
  The rules for applying cryptographic functions on SWIFTNet InterAct responses are:  
  
- ResponseControl: this is destined to SWIFTNet only. SWIFTNet delivers a ResponseDescriptor to the Requestor. Therefore, no server process to client process cryptographic operation, can be performed on it.  
  
- ResponseE2EControl: this element contains information to ensure reliable end-to-end messaging. No cryptographic operation can be performed on it.  
  
- ResponseHeader: this element can be signed (it is transferred unchanged to the Requestor).  
  
- ResponsePayload: can be encrypted and/or signed.  
  
- Crypto element(s): these relate to previously activated cryptographic operations on this Request. No cryptographic operations can be performed on these.  
  
## Receiving Requests with Cryptography  
 A server process may receive Requests that were subjected to cryptographic operations by the Requestor. The incoming Request contains all relevant information to enable the reverse cryptographic operations. The CryptoInternal information is such that the decryption and verification function will now effectively operate.  
  
 The server process will need to activate the security contexts of the DN for which decryption needs to take place  
  
 The Request will then be modified by the reverse cryptographic operations (verify, decrypt) in such a way that the original Request will be made available unaltered to the server process, as it was originally delivered by the client process to the cryptographic operations. For the Response, similar processing takes place. It is important to realize that verification of a signature will not only verify what was signed was not altered, but that it will authenticate whether the signer is genuine. This requires that the SignDN uses a valid certificate. A valid certificate is a certificate has not been revoked (a lookup in the Certificate Revocation List, kept centrally within SWIFTNet).  
  
## Activation  
 SWIFTNet Link can operate verification and decryption in automatic mode for all incoming Requests and incoming Responses. This means that SWIFTNet Link will automatically process (verify and decrypt) the last crypto block of all incoming Requests (server side) or incoming Responses (client side). The prerequisites are that the security context required for decryption (if decryption is requested) is opened and that SWIFTNet Link has been initialized in automatic mode (this setting to automatic mode is done on the Sw:InitRequest or Sw:HandleInitResponse, by setting the CryptoMode to "Automatic" or better still "Advanced" for InterAct. (We will always use “Advanced” for the InterAct Adapter, as this allows the client or server application to recover form unexpected encryption by the remote side, or from an expired certificate.  
  
 SWIFTNet Link operates signature and encryption automatically on one outgoing Request (or one outgoing Response) if the field RequestCrypto (ResponseCrypto) is initialized to “TRUE” in the RequestControl (ResponseControl) of the Request (Response).  
  
 In that case SWIFTNet Link processes the last crypto block. The prerequisites are that the security context required for signature (if signature is requested) is opened, that the crypto block is present in the Request with indication on the signature and encryption required, and that the RequestCrypto (ResponseCrypto) flag is set to “TRUE” in the RequestControl (ResponseControl). This is always done, irrespective of the CryptoMode used at initialization of the client or server.  
  
## See Also  
 [InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)   
 [InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md)   
 [InterAct Adapter Messages for Business Exchange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md)   
 [InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md)   
 [InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md)   
 [InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md)   
 [InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md)   
 [InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md)   
 [InterAct Adapter Non-Repudiation](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)