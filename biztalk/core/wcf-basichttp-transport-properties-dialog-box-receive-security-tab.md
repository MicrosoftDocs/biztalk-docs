---
title: "WCF-BasicHttp Transport Properties Dialog Box, Receive, Security Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-basichttp.transport.receive.security"
helpviewer_keywords: 
  - "WCF-BasicHttp adapters, properties"
  - "security, WCF-BasicHttp adapters"
  - "WCF-BasicHttp adapters, security"
  - "properties, WCF-BasicHttp adapters"
ms.assetid: 648016dc-fe56-4e73-addc-03714d7dc41c
caps.latest.revision: 31
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-BasicHttp Transport Properties Dialog Box, Receive, Security Tab
Use the **Security** tab to define the security capabilities of the WCF-BasicHttp receive adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Security mode**|Specify the type of security that is used. Valid values include the following:<br /><br /> -   **None**: Messages are not secured during transfer.<br />-   **Transport**: Security is provided using the HTTPS transport. The SOAP messages are secured using HTTPS. To use this mode, you must set up Secure Sockets Layer (SSL) in Microsoft Internet Information Services (IIS).<br />-   **Message**: Security is provided using SOAP message security over the HTTP transport. By default, the SOAP **Body** is encrypted and signed. The only valid **Message client credential type** for the WCF-Basic adapter is **Certificate**. This mode requires the HTTP transport. When using this security mode, the service certificate for this receive location needs to be provided through the **Service certificate - Thumbprint** property.<br />-   **TransportWithMessageCredential**: Integrity, confidentiality, and service authentication are provided by the HTTPS transport. To use this mode, you must set up Secure Sockets Layer (SSL) in Microsoft Internet Information Services (IIS).<br />-   **TransportCredentialOnly**: This mode does not provide message integrity and confidentiality. It provides HTTP-based client authentication. This mode should be used with caution. It should be used in environments where the transport security is provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure. If you select **Certificate** for the **Transport client credential type** property in this security mode, the service certificate for this receive location needs to be provided through the **Service certificate - Thumbprint** property.<br /><br /> The default is **None**.|  
|**Transport client credential type**|Specify the type of credential to be used when performing the client authentication. Valid values include the following:<br /><br /> -   **None**: No authentication occurs at the transport level.<br />-   **Basic**: Basic authentication. In Basic authentication, user names and passwords are sent in plain text over the network. You must create the domain or local user accounts corresponding to the credentials.<br />-   **Digest**: Digest authentication. This authentication method operates much like Basic authentication, except that passwords are sent across the network as a hash value for additional security. Digest authentication is available only on domains with domain controllers running Windows Server operating systems authentication. You must create the domain or local user accounts corresponding to client credentials.<br />-   **Ntlm**: NTLM authentication. Clients can send the credentials without sending a password to this receive location. You must create the domain or local user accounts corresponding to client credentials.<br />-   **Windows**: Windows integrated authentication. Windows Communication Foundation negotiates Kerberos or NTLM, preferring Kerberos if a domain is present. If you want to use Kerberos it is important to have the client identify the service with a service principal name (SPN). You must create the domain or local user accounts corresponding to client credentials.<br />-   **Certificate**: Client authentication using the client certificate. The CA certificate chain for the client X.509 certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the clients can be authenticated to this receive location. **Note:**  The **Transport client credential type** property must match the authentication scheme of the IIS virtual directory hosting this receive location. For example, if the property is set to **Windows**, you also need to enable **Integrated Windows authentication** for the virtual directory that hosts it. Similarly if the property is set to **None**, you must allow anonymous access to the virtual directory that hosts this receive location. <br /><br /> The default is **None**.|  
|**Message client credential type**|Specify the type of credential to be used when performing client authentication using message-based security. Valid values include the following:<br /><br /> -   **UserName**: Allow this receive location to require that clients be authenticated using the **UserName** credential. You must create the domain or local user accounts corresponding to the client credentials.<br />-   **Certificate**: Clients are authenticated to this receive location using the client certificate. The CA certificate chain for the client X.509 certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the clients can be authenticated to this receive location.<br /><br /> The default is **UserName**.|  
|**Algorithm suite**|Specify the message encryption and key-wrap algorithms. These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification. Possible values are:<br /><br /> -   **Basic128**: Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic128Rsa15**: Use Aes128 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **Basic128Sha256**: Use Aes256 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic128Sha256Rsa15**: Use Aes128 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />-   **Basic192**: Use Aes192 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic192Rsa15**: Use Aes192 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **Basic192Sha256**: Use Aes192 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic192Sha256Rsa15**: Use Aes192 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />-   **Basic256**: Use Aes256 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic256Rsa15**: Use Aes256 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **Basic256Sha256**: Use Aes256 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic256Sha256Rsa15**: Use Aes256 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />-   **TripleDes**: Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.<br />-   **TripleDesRsa15**: Use TripleDes encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **TripleDesSha256**: Use TripleDes for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **TripleDesSha256Rsa15**: Use TripleDes for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br /><br /> The default value is **Basic256**.|  
|**Service certificate -Thumbprint**|Specify the thumbprint of the X.509 certificate for this receive location that the clients use to authenticate the service. The thumbprint can be selected by navigating the **My** store in the **Current User** location with the **Browse** button. **Note:**  You must install the service certificate into the **Current User** location of the user account for the receive handler hosting this receive location. <br /><br /> Minimum length: 0<br /><br /> Maximum length: 40<br /><br /> The default is an empty string.|  
|**Use Single Sign-On**|Use Single Sign-On to retrieve client credentials to issue an SSO ticket. This option is valid only for the security configurations listed in the following section, "Enterprise Single Sign-On Supportability for the WCF-BasicHttp Receive Adapter."<br /><br /> The default value is cleared.|  
  
## Enterprise Single Sign-On Supportability for the WCF-BasicHttp Receive Adapter  
 The WCF-BasicHttp receive adapter can issue an SSO ticket from the SSO server only in the security configurations shown in the following table.  
  
|**Security mode**|**Transport client credential type**|**Message client credential type**|  
|-----------------------|------------------------------------------|----------------------------------------|  
|**Transport**|**Basic**|N/A|  
|**Transport**|**Digest**|N/A|  
|**Transport**|**Ntlm**|N/A|  
|**Transport**|**Windows**|N/A|  
|**Transport**|**Certificate**|N/A|  
|**Message**|N/A|**UserName**|  
|**TransportWithMessageCredential**|N/A|**UserName**|  
|**TransportCredentialOnly**|**Basic**|N/A|  
|**TransportCredentialOnly**|**Digest**|N/A|  
|**TransportCredentialOnly**|**Ntlm**|N/A|  
|**TransportCredentialOnly**|**Windows**|N/A|  
|**TransportCredentialOnly**|**Certificate**|N/A|  
  
## See Also  
 [How to Configure a WCF-BasicHttp Receive Location](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)   
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)   
 [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)   
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md)