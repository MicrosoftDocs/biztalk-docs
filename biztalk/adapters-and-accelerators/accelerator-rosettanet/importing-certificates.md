---
title: "Importing Certificates | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "importing certificates"
  - "certificates, importing"
ms.assetid: c2576f89-b5de-4250-9c54-74c8a218bb39
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing Certificates
This section describes how to import certificates, including where to import them from, where to store them, and what tools to use to import them.  
  
 There are two ways to import certificates. You can use the CertWizard tool or the Certificates snap-in for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).  
  
- CertWizard is a step-by-step command-line wizard that configures the use of the certificate based on the settings of switches. This tool is available in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK folder.  
  
- With the Certificates snap-in in MMC, you can import a certificate into the certificate store. However, this manual process requires that you configure the use of the certificate separately.  
  
  > [!IMPORTANT]
  >  To import or work with private certificates in MMC, the user who is logged on must have the user identity of the BizTalk Hosts. If not, you must run the **runas** command with the user switch and the host service account to start the Certificates MMC, for example, **runas /user:hostsvc mmc**. By running this command, you assume the user identity of the BizTalk Hosts (BizTalkServerApplication and BizTalkServerIsolatedHost).  
  
## In This Section  
  
-   [Certificate Sources and Stores](../../adapters-and-accelerators/accelerator-rosettanet/certificate-sources-and-stores.md)  
  
-   [Importing Certificates Using the CertWizard Utility](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)  
  
-   [Importing Certificates Using MMC](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md)