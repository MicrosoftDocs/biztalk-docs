---
title: "How to Configure BizTalk Server to Send Signed MIME or SMIME Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba42463b-2c12-4329-919e-aca427d14eee
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure BizTalk Server to Send Signed MIME or SMIME Messages
This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use certificates to send signed MIME/SMIME messages. The procedure below also applies to configuring the sending of signed messages over AS2 transport.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To configure BizTalk Server to send signed messages  
  
1. Create a pipeline to send signed messages, as follows:  
  
   > [!NOTE]
   >  This step is not necessary when configuring AS2 transport for sending signed messages because the AS2Send and AS2EdiSend pipelines that are included in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serve this function.  
  
   1. Create a send pipeline and then drag the MIME/SMIME Encoder pipeline component into the Encode stage of the pipeline.  
  
   2. In the **Properties** window, configure the MIME/SMIME Encoder pipeline component Signature type property to ClearSign or BlobSign.  
  
      > [!NOTE]
      >  If you are also using encryption, you can only select BlobSign.  
      > 
      > [!NOTE]
      >  You can configure the send pipeline component properties using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console after the pipeline has been deployed into a BizTalk group.  
      > 
      > [!NOTE]
      >  The MIME/SMIME Encoder pipeline component performs both encryption and digital signing (when configured to perform both functions). Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send encrypted and signed messages, you can use the same send pipeline. In other words, you do not have to create separate pipelines for encryption and digital signing.  
  
   3. Build and deploy the send pipeline.  
  
2. Configure the send port for sending signed messages, as follows:  
  
   1. Add the BizTalk assembly that you created containing the send pipeline to the BizTalk application that includes the send ports to send signed messages.  
  
      > [!NOTE]
      >  This step is not necessary when configuring AS2 transport for sending signed messages because the AS2Send and AS2EdiSend pipelines are included in the BizTalk EDI Application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
   2. Configure the send port in the BizTalk application with the send pipeline that you created in the previous procedure.  
  
3. Configure the group with a certificate for sending signed messages, as follows:  
  
   1. Configure the BizTalk group with the signing certificate that you installed by expanding the BizTalk group in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-clicking **BizTalk Group**, and then clicking **Properties**.  
  
   2. Click the Certificate tab, click **Browse**, select the appropriate certificate, and then click **OK**.  
  
## See Also  
 [Configuring Certificates for MIME or SMIME Messages](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)