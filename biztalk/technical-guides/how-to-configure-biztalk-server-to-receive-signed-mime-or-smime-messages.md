---
title: "How to Configure BizTalk Server to Receive Signed MIME or SMIME Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50570257-7bb6-4ede-9026-873eefd06483
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure BizTalk Server to Receive Signed MIME or SMIME Messages
This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use certificates to receive signed MIME/SMIME messages. The procedure below also applies to configuring the receiving of signed messages over AS2 transport.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To configure BizTalk Server to receive signed messages  
  
1. Create a pipeline to receive signed messages, as follows:  
  
   > [!NOTE]
   >  This step is not necessary when configuring AS2 transport for receiving signed messages because the AS2Receive and AS2EdiReceive pipelines that are included in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serve this function.  
  
   1. Create a receive pipeline and then drag the MIME/SMIME Decoder pipeline component into the Decode stage of the receive pipeline.  
  
   2. In the **Properties** window, configure the MIME/SMIME Decoder pipeline component properties.  
  
      > [!NOTE]
      >  You can configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You can configure different pipeline properties for each receive location in the BizTalk group.  
  
   3. Build and deploy the receive pipeline.  
  
2. Configure a receive location for receiving signed messages, as follows:  
  
   1. Add the BizTalk assembly that you created containing the receive pipeline to the BizTalk application including the receive locations to receive signed messages.  
  
      > [!NOTE]
      >  This step is not necessary when configuring AS2 transport for receiving signed messages because the AS2Receive and AS2EdiReceive pipelines are included in the BizTalk EDI Application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
   2. Configure the receive locations in the BizTalk application with the receive pipeline that you created in previous procedure.  
  
3. Configure the party with a certificate for receiving signed messages, as follows:  
  
   -   Open the **Party Properties** dialog box in the BizTalk Server Administration Console, click the **Certificate** tab, click **Browse**, select the appropriate certificate, and then click **OK**.  
  
       > [!NOTE]
       >  The certificate used to verify a signature for a party must be unique from the certificates used to verify signatures for other parties.  
  
## See Also  
 [Configuring Certificates for MIME or SMIME Messages](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)