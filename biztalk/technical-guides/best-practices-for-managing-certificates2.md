---
title: "Best Practices for Managing Certificates2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71fa00cc-2e0c-46b3-ae62-f130a5b5f4f5
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Managing Certificates
This section provides best practices for managing certificates in your Microsoft BizTalk Server environment.  
  
## Assess and Plan Your Use of Certificates  
 **Do a Threat Model Analysis of your environment**  
  
- Do a Threat Model Analysis (TMA) of your environment to determine whether signing or encryption certificates will help you mitigate security threats.  
  
  **Create a plan for public key certificates with partners**  
  
- Create a plan for sending public key certificates to and receiving public key certificates from partners. If you are not using signing certificates for party resolution, the public certificate can be attached to the message, in which case you do not need a copy of the certificate in your system beforehand.  
  
  **Establish guidelines with partners for submitting public keys**  
  
- As part of your Service Level Agreement (SLA) with your partner, establish guidelines for submitting public keys, notifying you when their certificates are about to expire, and notifying you when they revoke a certificate.  
  
## Install Certificates  
 **Download the certificate revocation list at set intervals**  
  
- Download the certificate revocation list (CRL) from your certification authority (CA) at set intervals. We recommend doing this once a week. The CRLs are downloaded automatically if there is a CA for the domain in which the BizTalk servers are joined.  
  
  **Verify signing certificates**  
  
- Make sure you verify the signing certificates against the certificate revocation list. For more information about how to verify the signing certificates, see [How to Configure the MIME/SMIME Decoder Pipeline Component](http://go.microsoft.com/fwlink/?LinkId=155145) (<http://go.microsoft.com/fwlink/?LinkId=155145>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
  **Manage certificates with partners**  
  
- Make certificate management part of your partner management practices. When you add or remove a party from the BizTalk Server environment, we recommend that you add or remove the certificates associated with that partner.  
  
  **Remove certificates before removing a host instance**  
  
- Before removing a host instance from a BizTalk server, remove the certificates in the personal store of the account under which the host instance is running.  
  
## Configure BizTalk Server to Use Certificates for MIME/SMIME  
 **Avoid denial of service attacks for digital signatures**  
  
- Determine what you want to do with messages when BizTalk Server cannot validate the digital signature. Setting the Authentication property on the receive port will help prevent denial of service attacks.  
  
  > [!NOTE]
  >  The Authentication - Drop messages and Authentication - Keep messages flags on the receive port require that the Party Resolution pipeline component be configured correctly, and that the parties are defined in BizTalk Server. For more information, see [Party Resolution Pipeline Component](http://go.microsoft.com/fwlink/?LinkId=155146) (<http://go.microsoft.com/fwlink/?LinkId=155146>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
  **Create separate receive locations for encrypted and unencrypted messages**  
  
- If you plan to receive MIME-encrypted messages from some partners and unencrypted messages from other partners, create separate receive locations in different hosts for encrypted and unencrypted messages. When you expect only MIME-encrypted messages, configure the Allow Non MIME Message option in the Decode MIME/SMIME pipeline component to No.  
  
## Configure a BizTalk Adapter to Use Certificates  
 **Test your connection to the target Web site**  
  
- If you are using SSL, ensure that you can connect to the target Web site with Microsoft Internet Explorer® before attempting to connect to the target Web site with the HTTP or SOAP transports. Verify that no dialog boxes are displayed in Internet Explorer when you connect to the target Web site. BizTalk Server has no mechanism for interfacing with any dialog boxes that might be displayed when connecting to the target web site. A dialog box may be displayed by Internet Explorer if the target Web site name does not match the name specified for the Web site in the SSL certificate or if the Root Certification Authority for the SSL certificate is not in the appropriate Trusted Root Certification Authorities store.  
  
  **Use the SSL Diagnostics tool to analyze SSL connection issues**  
  
- The SSL Diagnostics tool is an optional component of the IIS Diagnostics Toolkit. You can download the IIS Diagnostics Toolkit from the [Internet Information Services Diagnostics Tools](http://go.microsoft.com/fwlink/?LinkID=64426) page (http://go.microsoft.com/fwlink/?LinkID=64426).  
  
## Exporting a Certificate from One BizTalk Group to Another  
 **Ensure that an imported certificate is being used for its intended purpose**  
  
-   If you import a certificate into a group, the imported certificate must have a usage property that is consistent with its intended use. To check the usage property, double-click the certificate in the **Certificates Management Console** interface, and then click the **Details** tab of the **Certificate** dialog box. Then click the **All** option for the **Show** drop-down list, and then click to select the **Key Usage** and/or **Enhanced Key Usage** fields to verify the intended purpose. If BizTalk Server attempts to use a certificate for other than its intended purpose a runtime error will occur.