---
title: "How to Configure BizTalk Server for Receiving Encrypted Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd1e7e4c-f80c-468e-aa86-7c18406feead
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure BizTalk Server for Receiving Encrypted Messages
The following procedure lists the steps that you have to follow to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive encrypted messages.  
  
-   To create a pipeline to receive encrypted messages  
  
-   To configure the receive location for receiving encrypted messages  
  
## Prerequisites  
 Before configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s for receiving encrypted messages, you must perform the steps in [How to Install the Certificates for Encrypted Messages](../core/how-to-install-the-certificates-for-encrypted-messages.md).  
  
### To create a pipeline to receive encrypted messages  
  
1. In Solution Explorer in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select the project in which you want to create the pipeline.  
  
   1.  On the **File** menu, click **Add New Item**.  
  
   2.  In the **Add New Item** dialog box, expand BizTalk Project Items, click **Pipeline Files**, and then click the **Receive Pipeline** template.  
  
   3.  In the **Name** field, type a name for the pipeline.  
  
   4.  Click **Add**.  
  
        The new pipeline appears in Solution Explorer.  
  
2. Drag the MIME/SMIME Decoder pipeline component into the Decode stage of a receive pipeline.  
  
    ![MIME&#47;SMIME Decoder pipeline component](../core/media/bts-dev-mimesmimedecoder.gif "BTS_DEV_MIMESMIMEDecoder")  
  
   -   Configure the MIME/SMIME Decoder pipeline component properties in the **Properties** window. For more information about the MIME/SMIME decoder, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).  
  
   > [!NOTE]
   >  You can configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. You can configure different pipeline properties for each receive location in the BizTalk group. For more information, see [How to Configure Per-instance Pipeline Properties for a Receive Location](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md).  
   > 
   > [!NOTE]
   >  The MIME/SMIME Decoder pipeline component performs both decryption and digital signature validation (when configured to perform both functions). Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive encrypted and signed messages, you can use the same receive pipeline. In other words, you do not have to create separate pipelines for decryption and digital signature validation.  
  
3. Build and deploy the receive pipeline.  
  
### To configure the receive location for receiving encrypted messages  
  
1.  Add the BizTalk assembly that you created in previous procedure to the BizTalk Application including the receive locations to receive encrypted messages. For more information about how to add BizTalk assemblies, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
2.  Configure the receive locations in the BizTalk Application with the receive pipeline that you created in previous procedure. For more information about how to configure receive locations, see [How to Edit the Properties of a Receive Location](../core/how-to-edit-the-properties-of-a-receive-location.md).  
  
3.  Configure the host used as receive handler for the receive location with the decryption certificate that you installed in the procedure," To configure BizTalk hosts for receiving encrypted messages" in [How to Install the Certificates for Encrypted Messages](../core/how-to-install-the-certificates-for-encrypted-messages.md). For more information how to configure host properties, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).  
  
## See Also  
 [Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)   
 [How to Configure BizTalk Server for Sending Encrypted Messages](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md)   
 [Sending and Receiving Encrypted Messages](../core/sending-and-receiving-encrypted-messages.md)