---
title: "WCF-NetTcp Transport Properties Dialog Box, Receive, Security Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-nettcp.transport.receive.security"
helpviewer_keywords: 
  - "WCF-NetTcp adapters, security"
  - "properties, WCF-NetTcp adapters"
  - "WCF-NetTcp adapters, properties"
  - "security, WCF-NetTcp adapters"
ms.assetid: 51a99053-7248-498f-a3aa-62b615c364e6
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetTcp Transport Properties Dialog Box, Receive, Security Tab
Use the **Security** tab to define the security capabilities of the WCF-NetTcp receive adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Security mode**|Specify the type of security that is used. Valid values include the following:<br /><br /> -   **None**: Messages are not secured during transfer.<br />-   **Transport**: Transport security is provided using **TLS over TCP** or **SPNego**. It is possible to control the protection level with this mode. If you select **None** or **Certificate** for the **Transport client credential type** property in this security mode, you must supply the service certificate for this receive location through the **Service certificate - Thumbprint** property.<br />-   **Message**: Security is provided using SOAP message security. By default, the SOAP **Body** is encrypted and signed. This mode offers a variety of features, such as whether the service credentials are available at the client out of band, and the algorithm suite to use. If you select **None**, **UserName**, or **Certificate** for the **Message client credential type** property in this security mode, you must supply the service certificate for this receive location through the **Service certificate - Thumbprint** property.<br />-   **TransportWithMessageCredential**: Transport security is coupled with message security. Transport security is provided by **TLS over TCP** or **SPNego** and ensures integrity, confidentiality, and server authentication. If you select **Windows**, **UserName**, or **Certificate** for the **Message client credential type** property in this security mode, you must supply the service certificate for this receive location through the **Service certificate - Thumbprint** property. **Note:**      This security mode cannot be used with the **Transport client credential type** property, **None**.<br /><br /> The default is **Transport**.|  
|**Transport client credential type**|Specify the type of credential to be used when performing the client authentication. Valid values include the following:<br /><br /> -   **None**: No authentication occurs at the transport level. This credential type supports only **EncryptAndSign** for the **Transport protection level** property.<br />-   **Windows**: Windows integrated authentication of the client using SP Negotiation (Kerberos negotiation). You must create the domain or local user accounts corresponding to client credentials. In addition, the client's **userPrincipalName** element must be configured with the user account name running this receive handler.<br />-   **Certificate**: Client authentication using client certificates. To authenticate the client certificates, the CA certificate chain for the client certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer. This credential type supports only **EncryptAndSign** for the **Transport protection level** property.<br /><br /> The default is **Windows**.|  
|**Transport protection level**|Define security at the level of the TCP transport. Signing messages mitigates the risk of a third party tampering with the message while it is being transferred. Encryption provides data-level privacy during transport. Valid values include the following:<br /><br /> -   **None**: No protection.<br />-   **Sign**: Messages are signed.<br />-   **EncryptAndSign**: Messages are encrypted and signed.<br /><br /> The default value is **EncryptAndSign**.|  
|**Message client credential type**|Specify the type of credential to be used when performing client authentication using message-based security. Valid values include the following:<br /><br /> -   **None**: This allows the service to interact with anonymous clients. This indicates that this client does not provide any client credential.<br />-   **Windows**: Allow the SOAP exchanges to be under the authenticated context of a Windows credential. The client credential is passed through the SOAP **Header** element using the **WSS SOAP Message Security Kerberos Token Profile 1.0** protocol. You must create the domain or local user accounts corresponding to client credentials. In addition, the client's **userPrincipalName** element must be configured with the user account name running this receive handler.<br />-   **UserName**: Clients are authenticated to this receive location with a **UserName** credential. The credential is passed through the SOAP **Header** element using the **WSS SOAP Message Security UsernameToken Profile 1.0** protocol. You must create the domain or local user accounts corresponding to client credentials.<br />-   **Certificate**: Clients are authenticated to this receive location using the client certificate specified through the **Service certificate - Thumbprint** property. The credential is passed through the SOAP **Header** element using the **WSS SOAP Message Security X509 Token Profile 1.0** protocol. To authenticate the client certificates, the CA certificate chain for the client certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer. In addition, you must provide the service certificate for this location through the **Service certificate - Thumbprint** property.<br /><br /> The default is **Windows**.|  
|**Algorithm suite**|Specify the message encryption and key-wrap algorithms. These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification. Possible values are:<br /><br /> -   **Basic128**: Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic128Rsa15**: Use Aes128 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **Basic128Sha256**: Use Aes256 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic128Sha256Rsa15**: Use Aes128 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />-   **Basic192**: Use Aes192 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic192Rsa15**: Use Aes192 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **Basic192Sha256**: Use Aes192 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic192Sha256Rsa15**: Use Aes192 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />-   **Basic256**: Use Aes256 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic256Rsa15**: Use Aes256 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **Basic256Sha256**: Use Aes256 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic256Sha256Rsa15**: Use Aes256 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />-   **TripleDes**: Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.<br />-   **TripleDesRsa15**: Use TripleDes encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **TripleDesSha256**: Use TripleDes for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **TripleDesSha256Rsa15**: Use TripleDes for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br /><br /> The default value is **Basic256**.|  
|**Service certificate -Thumbprint**|Specify the thumbprint of the X.509 certificate for this receive location that the clients use to authenticate the service. The thumbprint can be selected by navigating the **My** store in the **Current User** location with the **Browse** button. **Note:**  You must install the service certificate into the **Current User** location of the user account for the receive handler hosting this receive location. <br /><br /> Minimum length: 0<br /><br /> Maximum length: 40<br /><br /> The default is an empty string.|  
|**Use Single Sign-On**|Specify whether to use Single Sign-On to retrieve client credentials to issue an SSO ticket. This option is valid only for the security configurations listed in the following section, "Enterprise Single Sign-On Supportability for the WCF -NetTcp Receive Adapter."<br /><br /> The default value is cleared.|  
  
## Enterprise Single Sign-On Supportability for the WCF-NetTcp Receive Adapter.  
 The WCF-NetTcp receive adapter can issue an SSO ticket from the SSO server only in the security configurations shown in the following table.  
  
|**Security mode**|**Transport client credential type**|**Message client credential type**|  
|-----------------------|------------------------------------------|----------------------------------------|  
|**Transport**|**Windows**|N/A|  
|**Message**|N/A|**Windows**|  
|**Message**|N/A|**UserName**|  
|**TransportWithMessageCredential**|N/A|**Windows**|  
|**TransportWithMessageCredential**|N/A|**UserName**|  
  
## See Also  
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md)   
 [How to Configure a WCF-NetTcp Receive Location](../core/how-to-configure-a-wcf-nettcp-receive-location.md)   
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)