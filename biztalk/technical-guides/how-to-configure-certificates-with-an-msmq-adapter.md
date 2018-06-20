---
title: "How to Configure Certificates with an MSMQ Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 922a171d-705f-4465-acda-212aa3797c57
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Certificates with an MSMQ Adapter
The MSMQ send adapter can help secure a connection with servers that accept or require client certificates. If a client certificate is specified, the MSMQ send adapter uses the certificate when connecting with servers that require or accept client certificates. If the client certificate is not specified and the destination server requires client certificates, the sender is not authenticated and the MSMQ send adapter fails to send the message and follows the standard retry logic.  

 The MSMQ send adapter uses the client certificate from the personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running. The certificate is specified by its thumbprint. If the MSMQ send adapter fails to load the certificate for any reason, the message that it was sending is suspended.  

 When using an MSMQ adapter to send an encrypted or signed message, configure the Certificate Thumbprint MSMQ transport property for the send port. In this property, specify the thumbprint of the certificate to use for message authentication. Use this property in combination with the Use Authentication property to verify the message. Use the User Name and Password properties to gain access to queues.  

## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

### To configure BizTalk Server to send messages over an MSMQ connection  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new MSMQ send port or open the properties for an existing MSMQ send port.  

2. Click **Configure** in the **Transport** section of the **Send Port Properties** dialog box.  

3. In the **MSMQ Transport Properties** dialog box, for **Authentication**, select **True**.  

4. For **Certificate thumbprint**, enter the appropriate thumbprint.  

5. Click **OK**, and then click **OK** again.
