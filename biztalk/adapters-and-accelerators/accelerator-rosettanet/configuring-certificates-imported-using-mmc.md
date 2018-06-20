---
title: "Configuring Certificates Imported Using MMC | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "decryption certificates"
  - "certificates, decryption certificates"
  - "certificates, signing certificates"
  - "importing certificates"
  - "signing certificates"
  - "certificates, importing"
ms.assetid: 64dbfbcf-6026-4c68-a93a-f483ec52deac
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Certificates Imported Using MMC
After you have imported certificates using the Certificates snap-in for the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC), you must configure their use. This requires configuring the BizTalk Group, the BizTalk Host and Isolated Host service accounts, Partner Interface Processes (PIPs), trading partner agreements, and partners. You must perform the following steps:  
  
> [!NOTE]
>  If you use the CertWizard utility to import and configure a certificate, you do not have to perform these manual steps.  
  
- Configure the use of a signing certificate for the home organization. This means that you use a private key to identify the home organization in outgoing messages. To do this, you configure the signing certificate for the BizTalk Group.  
  
- Configure the use of a decryption certificate for the home organization. This means that you use a private key, which corresponds to the partner's public key, to decrypt incoming messages. To do this, you configure the decryption certificate for each BizTalk Host and the BizTalk Isolated Host service accounts. You must enter the same decryption certificate for both the host and isolated host service accounts, which for [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] you must set to the same account.  
  
  > [!NOTE]
  >  The BizTalk Hosts and the Isolated Host must have the same decryption certificate so that they can both decrypt the same encrypted incoming messages. The BizTalk Isolated Host that runs the HTTP adapter must have the certificate to receive the messages, because it does not have access to the Host certificate. The BizTalk Host also must have the certificate to process the messages after [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] has received them.  
  
- Configure encryption and signing certificates for each partner. To do this, you enter the certificates on the **General** tab of the **Partner** properties page in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Management Console. These include a public-key encryption certificate to encrypt outgoing messages to a partner, and a public-key signing certificate to verify the partner's identity on incoming messages. For more information, see [Creating or Editing a Partner](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md).  
  
- Configure the encryption policy between a home organization and a trading partner. To do this, you configure the trading partner agreement on the **Protocol** tab of the **Agreement Properties** page in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console. For more information, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
### To configure the signing certificate for a BizTalk Group or the decryption certificate for a BizTalk Host  
  
1. Click **Start**, click **Run**, type **runas /user:\<host service\> mmc**, and then click **OK**.  
  
   > [!NOTE]
   >  For \<*host service*\>, type the name of the service that you associated with the host service when you installed [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
2. Type the password for \<*host service*\>, and then press ENTER.  
  
3. Click **Start**, point to **All Programs**, point to [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
4. Expand **Certificates - Current User**, expand **Personal**, and then click **Certificates**.  
  
5. In the right pane, double-click a private certificate.  
  
6. In the Certificate window, on the **Details** tab, click **Thumbprint**, and then select the hexadecimal identification number in the display window. Press CTRL+C to copy it.  
  
7. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
8. To configure the signing certificate for a BizTalk Group, right-click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**(Local)**, and then click **Properties**. Click in the text box to the right of **Thumbprint**, press CTRL+V to paste the thumbprint number into the text box, and then click **OK**.  
  
9. To configure the decryption certificate for a BizTalk Host, expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, expand **Hosts**, right-click the host that you want to configure, and then click **Properties**.  
  
10. On the **Certificate** tab, click in the text box to the right of **Thumbprint**, press CTRL+V to paste the thumbprint number into the text box, and then click **OK**.  
  
    > [!NOTE]
    >  You must configure the decrypting certificates on both the BizTalk Host (BizTalkServerApplication) and the BizTalk Isolated Host (BizTalkServerIsolatedHost).  
  
## See Also  
 [Managing Certificates](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)