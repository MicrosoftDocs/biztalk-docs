---
title: "How to Configure Certificates with an HTTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc2f454f-22b5-4113-9a23-e00a816d5e48
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Certificates with an HTTP Adapter
The HTTP send adapter can help secure a connection with servers that accept or require client certificates. If a client certificate is specified, the HTTP send adapter uses the certificate when connecting with servers that require or accept client certificates. If the client certificate is not specified and the destination server requires client certificates, the sender is not authenticated and the HTTP send adapter fails to send the message and follows the standard retry logic.  

 The HTTP send adapter uses the client certificate from the personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running. The certificate is specified by its thumbprint. If the HTTP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.  

 When using an HTTP adapter to send an encrypted or signed message, configure the SSL certificate thumbprint HTTP transport property for the send port. In this property, specify the thumbprint of the certificate to use for message authentication.  

## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

### To configure BizTalk Server to send messages over an HTTP connection  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new HTTP send port or open the properties for an existing HTTP send port.  

2. Click **Configure** in the Transport section of the **Send Port Properties** dialog box.  

3. Click **Authentication** in the **HTTP Transport Properties** dialog box.  

4. In **Authentication type**, select **Anonymous**, **Basic**, **Digest**, or **Kerberos**.  

5. If the authentication type is **Basic** or **Digest**, either select **Do not use Single Sign-On** (in which case you must specify the user name and password) or select **Use Single Sign-On** (in which case you must select the Affiliate Application).  

6. In **SSL client certificate thumbprint**, enter the appropriate thumbprint.  

7. Click **OK**, and then click **OK** again.
