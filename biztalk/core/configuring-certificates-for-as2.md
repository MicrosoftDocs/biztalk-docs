---
title: "Configuring Certificates for AS2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c160f294-7529-4e0a-876c-5827feaed067
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Certificates for AS2
To help secure AS2 data transfer using encryption and digital signatures, you must have the appropriate certificates installed, in addition to the appropriate AS2 configuration on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This topic describes the certificates required, how to configure them, and common issues with them.  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

## Certificates Required for AS2 Transport  
 To help secure AS2 data transfer, you must add the appropriate certificate to the appropriate certificate store, and associate the certificates with the appropriate BizTalk artifacts. The following certificates are used to help secure AS2 messages:  


|        Certificate Usage         |          Certificate Type           | Pipeline Component |                              User Context                              |                                                                                           Certificate Store                                                                                           |                                                                                                                                                                                                                                                                                                                                                            Where Defined                                                                                                                                                                                                                                                                                                                                                             |
|----------------------------------|-------------------------------------|--------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       Signature (outbound)       |       Own private key (.pfx)        |    AS2 encoder     |  Account used by the host instance associated with the send handler.   |    Current User\Personal store of each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that hosts an AS2 encoder pipeline as each host instance service account    | -   **Certificate** page of the **Group Properties** dialog box. This is the default signing certificate used when sending signed documents.<br />-   You can override the default certificate setting and instead use different certificates for different parties. You can do so by selecting **Override Group Signature Certificate** in the **Signature Certificate** page of the one-way agreement tab of the **Agreement Properties** dialog box, and specify a signing certificate. If this property is set, whichever AS2 message resolves to the agreement will be signed using the certificate provided in the **Signature Certificate** page and not by the certificate provided as part of the BizTalk Group properties. |
| Signature verification (inbound) | Trading partner's public key (.cer) |    AS2 decoder     | Account used by the host instance associated with the receive handler. | Local computer\Other People store of each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that hosts an AS2 decoder pipeline as each host instance service account |                                                                                                                                                                                                                                                           **Certificate** page of the **Party Properties** dialog box **Note:**  The certificate used to verify a signature for a party must be unique from the certificates used to verify signatures for other parties.                                                                                                                                                                                                                                                            |
|      Encryption (outbound)       | Trading partner's public key (.cer) |    AS2 encoder     |  Account used by the host instance associated with the send handler.   |                    Local computer\Other People store of each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that hosts an AS2 encoder pipeline                    |                                                                                                                                                                                                                                                                                                                                   **Certificate** page of the **Send Port Properties** dialog box                                                                                                                                                                                                                                                                                                                                    |
|       Decryption (inbound)       |       Own private key (.pfx)        |    AS2 decoder     | Account used by the host instance associated with the receive handler. |    Current User\Personal store of each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that hosts an AS2 decoder pipeline as each host instance service account    |                                                                                                                                                                                                                        The AS2 Decoder will determine the certificate based upon certificate information in the message.<br /><br /> For the BizTalk MIME Decoder, the certificate must be in the **Certificate** page of the host used for receiving the message. This is not necessary for the AS2 Decoder.                                                                                                                                                                                                                        |

## Certificate Signing for Outgoing Messages  
 Outgoing AS2 messages are signed using a default certificate defined as part of the BizTalk Group properties. However, there could be scenarios where the party receiving the messages wants the messages to be signed with a private certificate that they provide or expect a different certificate to be used when signing outgoing messages for them. This scenario of signing outgoing messages using other certificates is enabled if you select the **Override Group Signature Certificate** in the **Signature Certificate** page of the one-way agreement tab of the **Agreement Properties** dialog box, and specify a signing certificate. If a certificate is specified as part of the AS2 agreement for a party, that certificate is used for signing outgoing messages. If no certificate is defined for the party, the default certificate specified as part of the BizTalk Group properties is used.  

## Adding Certificates to the Certificate Stores  
 For more information, see the "Displaying the Certificates Management Console" section of [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md), as well as the [Certificate Wizard Utility](../core/certificate-wizard-utility.md) topic.  

> [!IMPORTANT]
>  The Personal certificate store will be available for message processing only if the user profile is loaded for the user whose logon credentials are associated with the host instance. The Personal store is used for signing and decryption certificates (the user's own private key). The user profile is loaded by default for the in-process host instance; however, the user profile is not loaded by default for the isolated host instance. You can have an application load the user profile for the isolated host. Alternatively, you can work around this issue by using the same logon for the in-process host instance and the isolated host instance.  

## Generating Certificates  
 Certificates can be obtained from a Certificate Authority (CA); however the steps to request a certificate can vary between CAs. Review the information provided on the Certificate Authority’s Web site before submitting any certificate requests.  

> [!IMPORTANT]
>  Certificates used for AS2 transport must have the attributes required for their intended use. For signing and signature verification, the **Key Usage** attribute of the certificate must be **Digital Signature**. For encryption and decryption, the **Key Usage** attribute of the certificate must be **Data Encipherment** or **Key Encipherment**. You can verify the **Key Usage** attribute by double-clicking the certificate, clicking the **Details** tab in the **Certificate** dialog box, and checking the **Key Usage** field.  

 You can also generate certificates in Windows Server 2008 by using Certificate Services, however your partner may only accept these certificates for test purposes as they are self-signed instead of signed by a public CA. For more information on using Certificate Services to request certificates, download **Windows Server 2008 Active Directory Certificate Services Step-By-Step Guide** from [Windows Server 2008 Step-by-Step Guides](http://go.microsoft.com/fwlink/?LinkId=187916) ([http://go.microsoft.com/fwlink/?LinkId=187916](http://go.microsoft.com/fwlink/?LinkId=187916)).  

### To configure a certificate for signing outgoing AS2 messages  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the **BizTalk Group** node, and then click **Properties**.  

2. In the console tree of the **Group Properties** dialog box, click **Certificate**.  

3. In the **Certificate** pane, click **Browse**, find the certificate you want to use for signing, and then click **OK**.  

   > [!NOTE]
   >  Instead of entering the common name of the certificate, you can enter just the thumbprint. You can get the thumbprint by double-clicking the certificate in the certificate store in MMC or in the file system, clicking the **Details** tab, clicking the **Thumbprint** field, and copying the thumbprint.  

4. Click **OK**.  

### To configure a certificate for signing outgoing AS2 messages for a specific party  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Parties** node. From the **Parties and Business Profiles** pane, from the **Agreements** section, right-click the agreement that is created for exchanging messages with a specific party, and click **Properties**.  

2. On a one-way agreement tab, click **Signature Certificates**.  

3. Select the **Override group signing certificate** check box to use the certificate provided in this page for signing outgoing AS2 messages and MDN.  

4. Click **Browse** to display the **Select Certificate** dialog box, where you select the signature certificate to apply to messages transmitted by this party.  

5. The **Common Name** text box displays a description of the selected certificate.  

6. The **Thumbprint** text box displays the thumbprint of certificate. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).  

7. Click **Remove Certificate** to remove the selected certificate.  

8. Click **OK** to validate the changes and then close the dialog box.  

### To configure a certificate for verifying the digital signature of an incoming AS2 messages  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, open the **BizTalk Group** node, and then click the **Parties** node.  

2. In the **Parties and Business Profiles** pane, right-click the party that you will be receiving signed messages from, and then click **Properties**.  

3. In the console tree, click **Certificate**.  

4. In the **Certificate** pane, click **Browse**, find the certificate you want to use for verifying the digital signature, and then click **OK**.  

   > [!NOTE]
   >  Instead of entering the common name of the certificate, you can enter just the thumbprint. You can get the thumbprint by double-clicking the certificate in the certificate store in MMC or in the file system, clicking the **Details** tab, clicking the **Thumbprint** field, and copying the thumbprint.  

5. Click **OK**.  

### To configure a certificate for encrypting an outgoing AS2 messages  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, open the **BizTalk Group** node, open the **Applications** node, and open the node of the **application** that contains the send port that you will be sending the encrypted message on.  

2. Open the **Send Ports** node, right-click the send port, and then click **Properties**.  

3. In the console tree, click **Certificate**.  

4. In the **Certificate** pane, click **Browse**, find the certificate that you want to use for encryption, and then click **OK**.  

   > [!NOTE]
   >  Instead of entering the common name of the certificate, you can enter just the thumbprint. You can get the thumbprint by double-clicking the certificate in the certificate store in MMC or in the file system, clicking the **Details** tab, clicking the **Thumbprint** field, and copying the thumbprint.  

5. Click **OK**.  

## See Also  
 [AS2 Security](../core/as2-security.md)   
 [Configuring Signing, Compression, and Encryption in AS2 Transport](../core/configuring-signing-compression-and-encryption-in-as2-transport.md)   
 [AS2 Solution Architecture](../core/as2-solution-architecture.md)   
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)