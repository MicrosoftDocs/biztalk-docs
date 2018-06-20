---
title: "Importing Certificates Using the CertWizard Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificates, root keys"
  - "certificates, public keys"
  - "certificates, private keys"
  - "importing certificates"
  - "public keys"
  - "private keys"
  - "CertWizard utility"
  - "certificates, importing"
  - "root keys"
ms.assetid: 0c54d7ab-69cf-4f4a-b976-6f740a41280b
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing Certificates Using the CertWizard Utility
This topic describes how to import a certificate by using CertWizard utility, a step-by-step command-line utility available in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK. This topic discusses importing a private, public, or root key. It describes the switches that you use to configure the certificate.  
  
 The CertWizard utility automates many of the steps that you would have to do manually by using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC). The CertWizard utility performs the **runas** command to open MMC as the host service account. If you do not add a **Useridentity** switch, it will detect and use the host service account, prompting you for a password. It stores and configures the certificate.  
  
 You can import multiple certificates at the same time by creating a batch file with multiple CertWizard utility commands.  
  
### To import a private key  
  
1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. At the command prompt, move to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK folder using the MS-DOS **CD** command, for example, type **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** .  
  
   > [!NOTE]
   >  For help with the CertWizard utility, type **CertWizard /?** at the command prompt.  
  
3. At the command prompt, type **CertWizard /Privatekey \<filename\>.pfx**, where \<*filename*\>.pfx contains the private certificate. To provide the password for the file, append **/Filepassword \<filepassword\>** to the command.  
  
4. If you want to import the certificate into a specific account used by the BizTalk Host, append **/Useridentity \<useridentity\> /Password \<password\>** to the command.  
  
5. If you want to designate a specific thumbprint in case the .pfx file contains more than one certificate, append **/Thumbprint \<thumbprint\>** to the command.  
  
6. If you want to configure the usage of the certificate, append **/Usage** to the command, and then append one of the following values:  
  
   -   Append **sign** to add the certificate's thumbprint as the signing certificate for the BizTalk Group. as set on the dialog box for Microsoft BizTalk Server (Local) in the BizTalk Administration Console.  
  
   -   Append **decrypt** to add the certificate's thumbprint as the decryption certificate for the BizTalk Hosts, as set on the certificate tab of the property pages for each host in the BizTalk Administration Console.  
  
   -   Append **both** to add the certificate's thumbprint for both the BizTalk Group's signing certificate and the BizTalk Host's decryption certificate.  
  
   -   Append **none** when you do not want to set the configuration for the BizTalk Group or the BizTalk Hosts.  
  
7. If you want to configure the certificate as exportable, append **/Exportable true**. To set the certificate as non-exportable, append **/Exportable false**, which is the default behavior.  
  
8. Press **Enter**.  
  
9. If you did not type one of the passwords required in the command, the tool prompts you for it. Type the password, and then press **Enter**.  
  
10. If the file contains multiple certificates, but you did not type a thumbprint in the command, the tool displays the available thumbprints, and prompts you to select one. Type the number of the thumbprint that you want, and then press **Enter**.  
  
     The tool imports the certificate into the \Personal\Certificates store for the user specified in the **/useridentity** switch. If you do not specify a user, the default user is the user identity for the BizTalkServerApplication and BizTalkServerIsolatedHost hosts.  
  
### To import a public key  
  
1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. At the command prompt, move to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK folder by using the MS-DOS **CD** command, for example, type **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.  
  
3. At the command prompt, type **CertWizard /Publickey \<filename\>.cer**, where \<*filename*\>.cer contains the public certificate.  
  
4. If you want to designate a thumbprint for the certificate in the .cer or .der file, append **/Thumbprint \<thumbprint\>** to the command.  
  
    The tool imports the certificate into the Certificates (Local Computer)\Other People\Certificates store, and sets its configuration.  
  
### To import a root key  
  
1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. At the command prompt, move to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK folder by using the MS-DOS **CD** command, for example, type **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.  
  
3. At the command prompt, type **CertWizard /Rootkey \<filename\>.cer**, where \<*filename*\>.cer contains the root certificate.  
  
4. If you want to designate a thumbprint for the certificate in the .cer or .der file, append **/Thumbprint \<thumbprint\>** to the command.  
  
    The tool imports the certificate into the Certificates (Local Computer)\Trusted Root Certification Authority\Certificates store, and sets its configuration.  
  
## See Also  
 [CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)   
 [Managing Certificates](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)