---
title: "Checklist: Installing and Configuring Certificates | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76a8f8f6-8d79-4caf-8fba-8cbcb251d461
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Installing and Configuring Certificates
This topic describes the steps involved in setting up certificates for use with BizTalk Server.  
  
|Steps|Reference|  
|-----------|---------------|  
|Assess your certificate requirements, and come to an agreement with your trading partner about your mutual responsibilities with respect to certificates.|"Assess and Plan Your Use of Certificates" section in [Best Practices for Managing Certificates](../Topic/Best%20Practices%20for%20Managing%20Certificates2.md)|  
|If you will be using the private key, request a private-public key pair for digital signatures from the certification authority (CA), and send the public key to your trading partner.<br /><br /> If you will be using the public key, have your trading partner request a private-public key pair for digital signatures from the CA, and send the public key to you.|[How to Install Certificates for BizTalk Server](../Topic/How%20to%20Install%20Certificates%20for%20BizTalk%20Server.md)|  
|Install the private or public key into the appropriate certificate store, and have your trading partner do the same.|-   [How to Install Certificates for BizTalk Server](../Topic/How%20to%20Install%20Certificates%20for%20BizTalk%20Server.md)<br />-   "Install Certificates" section of [Best Practices for Managing Certificates](../Topic/Best%20Practices%20for%20Managing%20Certificates2.md)|  
|If using the certificate for MIME/SMIME messages, configure BizTalk Server to use the certificate.|-   [Configuring Certificates for MIME or SMIME Messages](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)<br />-   "Configure BizTalk Server to Use Certificates for MIME/SMIME" section in [Best Practices for Managing Certificates](../Topic/Best%20Practices%20for%20Managing%20Certificates2.md)|  
|(Optional) If using the certificate with an adapter, configure the adapter to use the certificate.|-   [Configuring Certificates with Adapters](../Topic/Configuring%20Certificates%20with%20Adapters.md)<br />-   "Configure a BizTalk Adapter to Use Certificates" section of [Best Practices for Managing Certificates](../Topic/Best%20Practices%20for%20Managing%20Certificates2.md)|  
|(Optional) If using the certificate to perform party resolution, configure the party to use the certificate.|[How to Configure Certificates for Party Resolution](../Topic/How%20to%20Configure%20Certificates%20for%20Party%20Resolution.md)|  
|(Optional) If exporting the certificate from one BizTalk group to another, add the certificate to a BizTalk application; export the application to an .msi file; and then import the application into a different BizTalk group.|-   [How to Configure Certificates for Party Resolution](../Topic/How%20to%20Configure%20Certificates%20for%20Party%20Resolution.md)<br />-   [How to Export an Application to an .msi File](../Topic/How%20to%20Export%20an%20Application%20to%20an%20.msi%20File.md)<br />-   [How to Import an Application from an .msi File](../Topic/How%20to%20Import%20an%20Application%20from%20an%20.msi%20File.md)<br />-   "Exporting a Certificate from One BizTalk Group to Another" section of [Best Practices for Managing Certificates](../Topic/Best%20Practices%20for%20Managing%20Certificates2.md)|  
  
## See Also  
 [Best Practices for Managing Certificates](../Topic/Best%20Practices%20for%20Managing%20Certificates2.md)   
 [Known Issues with Certificates in BizTalk Server](../Topic/Known%20Issues%20with%20Certificates%20in%20BizTalk%20Server.md)