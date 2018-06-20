---
title: "Certificate Sources and Stores | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificates, certificate storage"
  - "importing certificates"
  - "certificates, certificate sources"
  - "certificates, importing"
ms.assetid: 3e98fb56-4368-46f3-9329-c44fed11f4fb
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Certificate Sources and Stores
This topic describes where to import certificates from, and where to store certificates.  
  
## Certificate Sources  
 You import certificates from the following files:  
  
- Private certificates from .pfx or .p12 files. After importing the certificates, store these files securely. If you import the private certificates using the CertWizard utility, you can set the **/Exportable** switch to `False`, which is the default setting, so that the private certificates cannot be exported from the store into a file. If you set the **/Exportable** switch to `True`, you can export these certificates to a file from the Certificates [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).  
  
- Public certificates from .cer or .der files. Partners send their certificates to you in these files.  
  
- Root certificates from .cer or .der files. Certification authorities send their root certificates to you in these files.  
  
## Certificate Storage  
 You import certificates into one of two Certificates stores on the local computer. You store public certificates in the **Certificates (Local Computer)** store. You can open the nodes of this store by opening the **Certificates (Local Computer)** node in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Management Console. You can access the **Certificates (Local Computer)** store if you have administrative permissions on the computer. Store public certificates in the following folders:  
  
- Home public certificates in the Personal folder in the **Certificates (Local Computer)** store  
  
- Partner public certificates in the Other People folder of the **Certificates (Local Computer)** store  
  
- Certificates from certification authorities in the Trusted Root Certification Authority folder of the **Certificates (Local Computer)** store  
  
  You store private certificates in the **Certificates - Current User** store. You can open the nodes of this store by opening the Management Console using the **runas** command with the host service account user. For more information, see [Importing Certificates](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates.md).  
  
## See Also  
 [Importing Certificates Using the CertWizard Utility](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)   
 [Importing Certificates Using MMC](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md)   
 [Importing Certificates &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/certificate-sources-and-stores.md)