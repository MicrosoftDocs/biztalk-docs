---
title: "How to Configure Certificates with a SOAP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20ee05c5-9cea-456d-bff6-49dd249f0ff4
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Certificates with a SOAP Adapter
The SOAP send adapter can help secure a connection with servers that accept or require client certificates. If you specify a client certificate, the SOAP send adapter uses the certificate when connecting with servers that require or accept client certificates. If you do not specify a client certificate and the destination server requires client certificates, the sender is not authenticated and the SOAP send adapter fails to send the message and follows the standard retry logic.  

 The SOAP send adapter uses the client certificate from the Personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running. The SOAP adapter specifies the certificate by its thumbprint. If the SOAP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.  

 When using a SOAP adapter to send an encrypted or signed message, configure the Client Certificate Thumbprint SOAP transport property for the send port.  

## Prerequisites  
 To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

### To configure BizTalk Server to send messages over a SOAP connection  

1. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new SOAP send port or open the properties for an existing SOAP send port.  

2. Click **Configure** in the **Transport** section of the **Send Port Properties** dialog box.  

3. On the **General** tab, in **Authentication type**, select **Anonymous**, **Basic**, **Digest**, or **NTLM**.  

4. If the authentication type is **Basic** or **Digest**, either select **Do not use Single Sign-On** (in which case you must specify the user name and password) or select **Use Single Sign-On** (in which case you must select the Affiliate Application).  

5. In **SSL client certificate thumbprint**, enter the appropriate thumbprint.  

6. Click **OK**, and then click **OK** again.
