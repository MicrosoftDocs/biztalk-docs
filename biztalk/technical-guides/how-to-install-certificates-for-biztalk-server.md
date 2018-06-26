---
title: "How to Install Certificates for BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70a89595-8828-4872-b78b-77e9b0b048b8
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Install Certificates for BizTalk Server
To help secure data transfer on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must add the appropriate certificate to the appropriate certificate store, and associate the certificates with the appropriate BizTalk artifacts. This topic describes how to display the Certificates Management Console interface for the Local Computer and Current User certificate stores, and how to install the appropriate certificate in the appropriate store.  

 The certificates shown in the following table are used to help sign, verify the signature for, encrypt, and decrypt messages.  

|Certificate Usage|Certificate Type|Certificate Store|  
|-----------------------|----------------------|-----------------------|  
|Signature (outbound)|Own private key (.pfx)|Current User\\<br />Personal store of each BizTalk server that hosts a MIME/SMIME encoder pipeline as each host instance service account|  
|Signature verification (inbound)|Trading partner's public key (.cer)|Local computer\Other People store of each BizTalk server that hosts a MIME/SMIME decoder pipeline as each host instance service account|  
|Encryption (outbound)|Trading partner's public key (.cer)|Local computer\Other People store of each BizTalk server that hosts a MIME/SMIME encoder pipeline|  
|Decryption (inbound)|Own private key (.pfx)|Current User\Personal store of each BizTalk server that hosts a MIME/SMIME decoder pipeline as each host instance service account|  

## Prerequisites  
 To perform the procedures in this topic you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

### To display the Certificates Management Console  

1.  Click **Start**, click **Run**, type **MMC**, and click **OK** to open the **Microsoft Management Console**.  

2.  Click the **File** menu, and then click **Add or Remove Snap-in** to display the **Add or Remove Snap-in** dialog box.  

3.  Click the **Add** button to display the **Add Standalone Snap-in** dialog box.  

4.  Select **Certificates** from the list of snap-ins, and then click **Add**.  

5.  Select **Computer account**, click **Next**, and then click **Finish**. This will add the **Certificates Management Console** interface for **Local Computer**.  

6.  Ensure that **Certificates** is still selected from the list of snap-ins, and then click **Add** again.  

7.  Select **My user account**, and then click **Finish**. This will add the **Certificates Management Console** interface for **Current User**.  

    > [!NOTE]  
    >  This displays the **Certificates Management Console** for the account that you are currently logged on as. If you need to import certificates into the Personal store for a service account then you should log on with the service account credentials first.  

8.  Click the **Close** button on the **Standalone Snap-in** dialog box.  

9. Click the **OK** button on the **Add or Remove Snap-in** dialog box.  

### To install a certificate for receiving encrypted messages  

1. Request a private-public key pair for digital signatures from the certification authority (CA) for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use.  

2. Send to the partner the public key for encryption.  

3. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on as the service account for the host instance running the handler that will receive messages from the partner. Install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] private key certificate for decrypting messages in the personal store for the service account.  

   > [!NOTE]
   >  For more information about the procedure used to install certificates for encryption, see [How to Install the Certificates for Encrypted Messages](http://go.microsoft.com/fwlink/?LinkId=155156) (<http://go.microsoft.com/fwlink/?LinkId=155156>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help. For more information about the tool used to import a certificate into the certificate store, see [Certificate Wizard Utility](http://go.microsoft.com/fwlink/?LinkId=155157) (<http://go.microsoft.com/fwlink/?LinkId=155157>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  

4. Have the partner install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] public key certificate for encrypting messages in the appropriate store. If the partner is using Windows 2000 Server, Windows Server 2003, or Windows Server 2008, they should install the public key in the Other People store.  

### To install a certificate for sending encrypted messages  

1. Have the partner request a private-public key pair for encryption from the certification authority (CA).  

2. Have the partner send you its public key for encrypting messages to be sent to the partner.  

3. Have the partner install the private key certificate for decrypting messages in the appropriate store. If the partner is using Windows 2000 Server, Windows Server 2003, or Windows Server 2008, they should install the private key in the personal certificate store.  

   > [!NOTE]
   >  For more information about the procedure used to install certificates for encryption, see [How to Install the Certificates for Encrypted Messages](http://go.microsoft.com/fwlink/?LinkId=155156) (<http://go.microsoft.com/fwlink/?LinkId=155156>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help. For more information about the tool used to import a certificate into the certificate store, see [Certificate Wizard Utility](http://go.microsoft.com/fwlink/?LinkId=155157) (<http://go.microsoft.com/fwlink/?LinkId=155157>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  

4. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on to the server that has a host instance running a handler that will send messages to the partner. Install the partner's public key certificate for encrypting messages sent to the partner in the Other People store.  

### To install a certificate for receiving signed messages  

1. Have the partner request a private-public key pair for digital signatures from the certification authority (CA).  

2. Have the partner send you its public key for digital signatures.  

3. Have the partner install its private key certificate for signing messages in the appropriate store. If they are using Windows 2000 Server, Windows Server 2003, or Windows Server 2008, have them install the private key in the personal store for the account that will sign messages sent to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

   > [!NOTE]
   >  For more information about the procedure used to install certificates for encryption, see [How to Install the Certificates for Encrypted Messages](http://go.microsoft.com/fwlink/?LinkId=155156) ([http://go.microsoft.com/fwlink/?LinkId=155156](http://go.microsoft.com/fwlink/?LinkId=155156)) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help. For more information about the tool used to import a certificate into the certificate store, see [Certificate Wizard Utility](http://go.microsoft.com/fwlink/?LinkId=155157) (<http://go.microsoft.com/fwlink/?LinkId=155156>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  

4. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on to the server that has a host instance running a handler that will receive messages from the partner. Install the partner's public key certificate to verify their signature in the Other People store.  

### To install a certificate for sending signed messages  

1. Request a private-public key pair for digital signatures from the certification authority (CA) for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use.  

2. Send to the partner the public key for digital signatures.  

3. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on as the service account for the host instance running the handler that will send messages to the partner. Install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] private key certificate for signing messages in the personal store for the service account.  

   > [!NOTE]
   >  For more information about the procedure used to install certificates for encryption, see [How to Install the Certificates for Encrypted Messages](http://go.microsoft.com/fwlink/?LinkId=155156) (<http://go.microsoft.com/fwlink/?LinkId=155156>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help. For more information about the tool used to import a certificate into the certificate store, see [Certificate Wizard Utility](http://go.microsoft.com/fwlink/?LinkId=155157) (<http://go.microsoft.com/fwlink/?LinkId=155157>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  

4. Have the partner install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] public key certificate for verifying its digital signature in the appropriate store. If the partner is using Windows 2000 Server, Windows Server 2003, or Windows Server 2008, they should install the public key in the Other People store.
