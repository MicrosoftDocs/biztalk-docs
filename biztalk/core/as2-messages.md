---
title: "AS2 Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1fac8418-3c07-4513-94aa-e7a25087d789
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Messages
This topic describes an AS2 message, including its structure, its context properties, and its headers.  
  
## Structure of an AS2 Message  
 In BizTalk Server, AS2 messages are structured according to [RFC 4130, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).  
  
 The basic structure of an AS2 message consists of MIME format inside an HTTP message with additional AS2-specific headers. The nature of the message beneath the HTTP, AS2, and MIME headers depends upon the type of message:  
  
- **Signed** – If the message is signed, a signature wrapper is added around the document payload.  
  
- **Compressed** – If the message is compressed, a compression wrapper is added around the document and signature payloads.  
  
- **Encrypted** – If the message is encrypted, an encryption wrapper is added around the document, signature, and compression payloads.  
  
  The message structure of an AS2 message, based upon encryption, signature, and compression is shown in the table below.  
  
|AS2 Message Options|Message Structure|  
|-------------------------|-----------------------|  
|- No compression<br /><br /> - No encryption<br /><br /> - No signature|`HTTP, AS2, MIME Header      EDI/XML Payload`|  
|- Compressed<br /><br /> - No encryption<br /><br /> - No signature|`HTTP, AS2, MIME Header      PKCS7-MIME Compression           EDI/XML Payload (compressed)`|  
|- Signed<br /><br /> - No compression<br /><br /> - No encryption|`HTTP, AS2, MIME Header       MIME Security Multipart (signed)           EDI/XML Payload           CMS-PKCS7 Signature`|  
|- Signed<br /><br /> - Compressed<br /><br /> - No encryption|`HTTP, AS2, MIME Header       PKCS7-MIME Compression           MIME Security Multipart (signed)(compressed)                EDI/XML Payload (compressed)                CMS-PKCS7 Signature (compressed)`|  
|- Encrypted<br /><br /> - No compression<br /><br /> - No signature|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           EDI/XML Payload (encrypted)`|  
|- Compressed<br /><br /> - Encrypted<br /><br /> - No signature|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                EDI/XML Payload (compressed)(encrypted)`|  
|- Encrypted<br /><br /> - Signed<br /><br /> - No compression|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           MIME Security Multiparts (signed)(encrypted)                EDI/XML Payload (encrypted)                CMS-PKCS7 Signature (encrypted)`|  
|- Compressed<br /><br /> - Encrypted<br /><br /> - Signed|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                MIME Security Multiparts (signed)(compressed)(encrypted)                     EDI/XML Payload (compressed)(encrypted)                     CMS-PKCS7 Signature (compressed)(encrypted)`|  
  
 If the document payload consists of multiple documents, they are stored within a multipart/related MIME envelope as described in RFC 2387. A Content-Disposition MIME header can be used to specify the filename of each document within the message.  
  
 The following table shows the message structure of an AS2 message that contains multiple attachments, based upon the message encryption, signature, and compression options.  
  
|AS2 Message Options|Message Structure|  
|-------------------------|-----------------------|  
|- No compression<br /><br /> - No encryption<br /><br /> - No signature|`HTTP, AS2, MIME Header      MIME Multipart/related           EDI/XML Payloads`|  
|- Compressed<br /><br /> - No encryption<br /><br /> - No signature|`HTTP, AS2, MIME Header      PKCS7-MIME Compression           MIME Multipart/related                EDI/XML Payload (compressed)`|  
|- Signed<br /><br /> - No compression<br /><br /> - No signature|`HTTP, AS2, MIME Header       MIME Security Multipart (signed)           MIME Multipart/related                EDI/XML Payload           CMS-PKCS7 Signature`|  
|- Compressed<br /><br /> - Signed<br /><br /> - No encryption|`HTTP, AS2, MIME Header       PKCS7-MIME Compression           MIME Security Multipart (signed)(compressed)                MIME Multipart/related (compressed)                     EDI/XML Payload (compressed)                CMS-PKCS7 Signature (compressed)`|  
|- Encryption<br /><br /> - No compression<br /><br /> - No signature|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           MIME Multipart/related (encrypted)                EDI/XML Payload (encrypted)`|  
|- Compressed<br /><br /> - Encrypted<br /><br /> - No signature|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                MIME Multipart/related                     EDI/XML Payload (compressed)(encrypted)`|  
|- Encrypted<br /><br /> - Signed<br /><br /> - No compression|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           MIME Security Multiparts (signed)(encrypted)                MIME Multipart/related                     EDI/XML Payload (encrypted)                CMS-PKCS7 Signature (encrypted)`|  
|- Compressed<br /><br /> - Encrypted<br /><br /> - Signed|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                MIME Security Multiparts (signed)(compressed)(encrypted)                     MIME Multipart/related                          EDI/XML Payload (compressed)(encrypted)                     CMS-PKCS7 Signature (compressed)(encrypted)`|  
  
## AS2 Context Properties  
 Context properties used in processing AS2 messages include properties that can be promoted as well as properties that are not publicly exposed, but can be viewed in suspended and tracked messages. For a list of AS2 context properties, see [AS2 Context Properties](../core/as2-context-properties.md).  
  
## AS2 Headers  
 The AS2 headers in AS2 messages describe the receiving and sending parties, and provide the information that the receiving party needs to send an MDN response. The receiving party will use the MDN headers unless the **Use agreement settings for validation and MDN instead of message header** property is selected in the AS2 agreement, or if the information is not available in the agreement properties.  
  
 The AS2-From header, AS2-To header, and MessageID context property uniquely describe an AS2 message. They are also used to correlate an MDN to the AS2 message that it is responding to.  
  
 These headers are listed (in alphabetical order) in the following table:  
  
|AS2 Header|Required/Optional|Values|  
|----------------|------------------------|------------|  
|AS2-Version|Optional|"1.1"|  
|AS2-From|Required|Name of the company that sent that the AS2 message.<br /><br /> Values: string, printable ASCII, 1 to 128 chars in length|  
|AS2-To|Required|Name of the company that the AS2 message is sent to.<br /><br /> Values: string, printable ASCII, 1 to 128 chars in length|  
|AS2-Text|Required|Text (in this header in the message)<br /><br /> Values: string, printable ASCII, 1 to 128 chars in length|  
|Disposition-Notification-To|Required|When present, serves as a request for an MDN to be returned. If it is accompanied by a receipt-delivery-option header, then it is a request for an asynchronous MDN. If not, then it is a request for a synchronous MDN.<br /><br /> When not present, an MDN is not required.<br /><br /> Value: a mail address that must be present. However, the address must not be used to identify where to return the MDN. The receiving application must ignore the mail address and must not complain about address syntax violations.|  
|EDIINT-Features|Required|Indicates the features supported by the originating system. BizTalk uses this header to indicate support for multiple attachments.<br /><br /> Value: “MA”|  
|Receipt-Delivery-Option|Required|Indicates the URL that the MDN should be sent to. When Receipt-Delivery-Option is present, Disposition-notification-to serves as a request for an asynchronous MDN. Receipt-Delivery-Option must always be accompanied by Disposition-Notification-To.<br /><br /> When Receipt-Delivery-Option is not present, and Disposition-notification-to is present, Disposition-notification-to serves as a request for a synchronous MDN.<br /><br /> Values: a URL string.|  
|signed-receipt-protocol<br /><br /> (in Disposition-Notification-Options)|Optional|When set to "pcks7-signature", is used to request a signed receipt from the receiving party, and indicates the format in which the signed receipt should be returned to the requester.<br /><br /> Values: optional, pcks7-signature|  
|signed-receipt-micalg<br /><br /> (in Disposition-Notification-Options)|Optional|A list of MIC algorithms preferred by the requester for use in signing the returned receipt. The list of MIC algorithms should be honored by the receiving party from left to right.<br /><br /> Values: optional, MD5 or SHA1|  
  
 For incoming messages, the AS2EdiReceive and AS2Receive receive pipelines validate the values of the Signed Receipt Protocol and Signed Receipt MIC Algorithm from the AS2 agreement properties.  
  
 For outgoing AS2 messages, the AS2EdiSend and AS2Send send pipelines populate the above AS2 headers from values entered in the AS2 agreement (with the exception of the AS2-Version, which is hardcoded as 1.1).  
  
 **Request for MDN**  
  
 A request that the receiving party return an MDN (Message Disposition Notification) is made by placing the following header in the message to be sent:  
  
 MDN-request-header = "Disposition-notification-to"  ":"  mail-address  
  
 The mail address is not used to identify where to return the MDN. Receiving applications must ignore the value, and not post an error about address syntax violations.  
  
## See Also  
 [MDN Messages](../core/mdn-messages.md)