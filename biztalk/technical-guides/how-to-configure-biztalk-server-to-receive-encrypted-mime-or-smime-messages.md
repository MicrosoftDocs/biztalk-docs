---
title: "How to Configure BizTalk Server to Receive Encrypted MIME or SMIME Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d72002c8-6bd8-458f-8149-1c0c4cbbb682
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure BizTalk Server to Receive Encrypted MIME or SMIME Messages
This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use certificates to receive encrypted MIME/SMIME messages. The procedure below also applies to configuring the receiving of encrypted messages over AS2 transport.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To configure BizTalk Server to receive encrypted messages  
  
1. Create a pipeline to receive encrypted messages, as follows:  
  
   > [!NOTE]
   >  This step is not necessary when configuring AS2 transport for receiving encrypted messages because the AS2Receive and AS2EdiReceive pipelines that are included in BizTalk Server serve this function.  
   > 
   > [!NOTE]
   >  The MIME/SMIME Decoder pipeline component performs both decryption and digital signature validation (when configured to perform both functions). Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive encrypted and signed messages, you can use the same receive pipeline. In other words, you do not have to create separate pipelines for decryption and digital signature validation.  
  
   1. Create a receive pipeline and then drag the MIME/SMIME Decoder pipeline component into the Decode stage of the pipeline.  
  
   2. In the **Properties** window, configure the MIME/SMIME Decoder pipeline component properties.  
  
      > [!NOTE]
      >  Configuring the MIME/SMIME Decoder pipeline component properties includes setting the Check Revocation List property to True if you want to check the certificate revocation list for the certificates that senders use for signing messages that are being sent to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Disabling this option increases the performance of the component. The certificate revocation list associated with a certificate is downloaded from the appropriate certificate services Web site. If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot connect to the remote Web site, the message fails in the pipeline.  
      > 
      > [!NOTE]
      >  You can configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You can configure different pipeline properties for each receive location in the BizTalk group.  
  
   3. Build and deploy the receive pipeline.  
  
2. Configure the receive location for receiving encrypted messages, as follows:  
  
   1. Add the BizTalk assembly that you created containing the receive pipeline to the BizTalk application including the receive locations to receive encrypted messages.  
  
      > [!NOTE]
      >  This step is not necessary when configuring AS2 transport for receiving encrypted messages because the AS2Receive and AS2EdiReceive pipelines are included in the BizTalk EDI Application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
   2. Configure the receive locations in the BizTalk application with the receive pipeline that you created in the previous step.  
  
3. Configure the host used as the receive handler for the receive location with the decryption certificate, as follows:  
  
   1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click a BizTalk host that is the handler for receiving the encrypted messages, and then click **Properties**.  
  
      > [!NOTE]
      >  This procedure does not apply for AS2 transport available with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. It applies for the BizTalk MIME Decoder, not the AS2 Decoder. The AS2 Decoder will determine the certificate based on certificate information in the message.  
  
   2. In the **Host Properties** dialog box, click **Certificate**, and then click **Browse**.  
  
      > [!NOTE]
      >  The above procedure enables you to configure your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment so that only certain hosts can receive and process particular messages. When you configure a host with the thumbprint of a certificate to use for message decoding and decryption, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] creates an application property for that host in the MessageBox database. Secure messages that are received and decrypted using this thumbprint are then only routed to this and other hosts that are configured with this thumbprint.  
  
   3. In the **Select Certificate** dialog box, select the decryption certificate that you installed, and then close all the dialog boxes.  
  
## See Also  
 [Configuring Certificates for MIME or SMIME Messages](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)