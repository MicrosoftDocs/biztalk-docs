---
title: "How to Configure BizTalk Server to Send Encrypted MIME/SMIME Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14f67152-5f80-4040-a9d6-0819fab7fcb5
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure BizTalk Server to Send Encrypted MIME/SMIME Messages
This topic describes how to configure BizTalk Server to use certificates to send encrypted MIME/SMIME messages. The procedure below also applies to configuring the sending of encrypted messages over AS2 transport.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.  
  
### To configure BizTalk Server to send encrypted messages  
  
1. Create a pipeline to send encrypted messages, as follows:  
  
   > [!NOTE]
   >  This step is not necessary when configuring AS2 transport for sending encrypted messages because the AS2Send and AS2EdiSend pipelines that are included in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serve this function.  
  
   1.  Create a send pipeline and then drag the MIME/SMIME Encoder pipeline component into the Encode stage of the pipeline.  
  
   2.  In the **Properties** window, configure the MIME/SMIME Encoder pipeline component Enable encryption property to **True**.  
  
       > [!NOTE]  
       >  You can configure the send pipeline component properties using the BizTalk Server Administration console after the pipeline has been deployed into a BizTalk group.  
  
   3.  Build and deploy the send pipeline.  
  
2. Configure the send port for sending encrypted messages, as follows:  
  
   1.  Add the BizTalk assembly that you created containing the send pipeline to the BizTalk application including the receive locations to receive encrypted messages.  
  
       > [!NOTE]  
       >  This step is not necessary when configuring AS2 transport for sending encrypted messages because the AS2Send and AS2EdiSend pipelines are included in the BizTalk EDI Application.  
  
   2.  Configure the send port in the BizTalk Application with the send pipeline that you created in the previous procedure.  
  
   3.  Assign the encryption certificate that you installed by right-clicking the send port, clicking **Properties**, and then clicking **Certificate**. Click **Browse**, browse to the certificate that you want to assign to this send port, and then click **OK**.  
  
       > [!NOTE]  
       >  If the certificate does not exist on the local computer, in the **Thumbprint** box, type or paste the certificate thumbprint, and then click **OK**. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.