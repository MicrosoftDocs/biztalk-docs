---
title: "Importing Certificates Using MMC | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificates, public keys"
  - "certificates, private keys"
  - "importing certificates"
  - "public keys"
  - "private keys"
  - "certificates, importing"
ms.assetid: 58fb1711-e295-4aa6-902e-e28e4a2cd921
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing Certificates Using MMC
This topic describes how to import a digital certificate that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses to authenticate a trading partner, decrypt an incoming message, or encrypt or sign an outgoing message.  
  
 This procedure uses the Certificates snap-in for the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC). This manual process imports a certificate into the certificate store, requiring you to configure certificate use separately. You can also import a certificate by using the CertWizard utility that automatically configures certificate use for you.  
  
 To import private certificates, you must use the user accounts under which the BizTalk Hosts run.  
  
### To import a public-key certificate  
  
1. Copy the public-key (.cer) certificate file to a location on the hard disk of the server to which you are copying certificates.  
  
2. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
3. In the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, expand **Certificates (Local Computer)**. The logged-in user must have administrative permissions to the computer.  
  
4. Right-click **Other People**, point to **All Tasks**, and then click **Import**.  
  
5. On the **Certificate Import Wizard Welcome** page, click **Next**.  
  
6. On the **File to Import** page, click **Browse** and locate the folder that contains the certificate files. Select the file from which you want to import the certificate, and then click **Open**.  
  
7. On the **Certificate store** page, select either **Automatically select the certificate based on the type of certificate** or **Place all certificates in the following store**. If you select **Place all certificates in the following store**, click **Browse**, select the certificate store, click **OK**, and then click **Next**.  
  
8. Click **Finish**.  
  
### To import a private-key certificate  
  
1. Copy private-key (.pfx) certificate files to a location on the hard disk of the server to which you are copying certificates.  
  
2. Click **Start**, click **Run**, type **run as /user:\<host service\> mmc**, and then click **OK**.  
  
   > [!NOTE]
   >  For \<*host service*\>, type the name of the service that was automatically selected for the host service when you installed [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
3. Type the password for \<*host service*\>, and then press **Enter**.  
  
4. In [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console, on the **File** menu, click **Add/Remove Snap-in**.  
  
5. In the Add/Remove Snap-in dialog box, click **Add**.  
  
6. In the Add Standalone Snap-in dialog box, select **Certificates**, click **Add**, click **Close**, and then click **OK**.  
  
7. In [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console, expand **Certificates - Current User**, right-click **Personal**, point to **All Tasks**, and then click **Import**.  
  
8. On the **Certificate Import Wizard Welcome** page, click **Next**.  
  
9. On the **File to Import** page, click **Browse** and locate the folder that contains the .pfx certificate file that contains the certificate that you want to import. Select the appropriate file, and then click **Open**.  
  
10. On the **Password** page, in the **Password** box, type the password for the private-key file.  
  
11. Select **Enable strong private key protection** or **Mark this key as exportable**, and then click **Next**.  
  
12. On the **Certificate store** page, select either **Automatically select the certificate based on the type of certificate** or **Place all certificates in the following store**. If you select **Place all certificates in the following store**, click **Browse**, select the store, click **OK**, and then click **Next**.  
  
13. On the **Completing the Certificate Import Wizard** page, click **Finish**.  
  
## See Also  
 [Configuring Certificates Imported Using MMC](../../adapters-and-accelerators/accelerator-rosettanet/configuring-certificates-imported-using-mmc.md)   
 [CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)