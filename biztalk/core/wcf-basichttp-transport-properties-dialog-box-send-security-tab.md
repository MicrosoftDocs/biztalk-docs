---
title: "WCF-BasicHttp Transport Properties Dialog Box, Send, Security Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-basichttp.transport.send.security"
helpviewer_keywords: 
  - "WCF-BasicHttp adapters, properties"
  - "security, WCF-BasicHttp adapters"
  - "WCF-BasicHttp adapters, security"
  - "properties, WCF-BasicHttp adapters"
ms.assetid: c3f47362-fb58-4d56-82e4-a79f6e3bdc26
caps.latest.revision: 43
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-BasicHttp Transport Properties Dialog Box, Send, Security Tab
Use the **Security** tab to define the security capabilities of the WCF-BasicHttp send adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Security mode**|Specify the type of security that is used. Valid values include the following:<br /><br /> -   **None**: Messages are not secured during transfer.<br />-   **Transport**: Security is provided using the HTTPS transport. The SOAP messages are secured using HTTPS. The CA certificate chain for the service's X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port using the service's certificate.<br />-   **Message**: Security is provided using SOAP message security. By default, the SOAP **Body** element is encrypted and signed. The only valid **Message client credential type** for the WCF-BasicHttp send adapter is **Certificate**. This mode requires the HTTP transport.<br />-   **TransportWithMessageCredential**: Integrity, confidentiality, and service authentication are provided by the HTTPS transport. The CA certificate chain for the service's X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store on this computer so that the service can be authenticated to the send port using the service's certificate. The send port authentication is provided by SOAP message security.<br />-   **TransportCredentialOnly**: This mode does not provide message integrity and confidentiality. It provides HTTP-based client authentication. This mode should be used with caution. It should be used in environments where the transport security is provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.<br /><br /> The default is **None**.|  
|**Transport client credential type**|Specify the type of credential to be used when performing the send port authentication. Valid values include the following:<br /><br /> -   **None**: No authentication occurs at the transport level.<br />-   **Basic**: Basic authentication. In Basic authentication, user names and passwords are sent in plain text over the network. This option requires configuring the **Client credentials** property.<br />-   **Digest**: Digest authentication. This authentication method operates much like Basic authentication, except that passwords are sent across the network as a hash value for additional security. Digest authentication is available only on domains with domain controllers running Windows Server operating systems authentication. This option requires configuring the **Client credentials** property.<br />-   **Ntlm**: NTLM authentication. The user account under which this send port runs is used for services to authenticate this send port.<br />-   **Windows**: Windows integrated authentication. The user account under which this send port runs is used for services to authenticate this send port.<br />-   **Certificate**: Client authentication using the client certificate specified through the **Client certificate - Thumbprint** property. When using this credential type, the service certificate needs to be provided through the **Service certificate - Thumbprint** property.<br /><br /> The default is **None**.|  
|**Message client credential type**|Specify the type of credential to be used when performing client authentication using message-based security. Valid values include the following:<br /><br /> -   **UserName**: This send port is authenticated to the service with a **UserName** credential. For the WCF-BasicHttp send adapter, this is not supported.<br />-   **Certificate**: This send port is authenticated to services using the client certificate specified through the **Client certificate - Thumbprint** property. In addition, when using this credential type, the service certificate needs to be provided through the **Service certificate - Thumbprint** property.<br /><br /> The default is **UserName**.|  
|**Algorithm suite**|Specify the message encryption and key-wrap algorithms. These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification. Possible values are:<br /><br /> -   **Basic128**: Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic128Rsa15**: Use Aes128 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **Basic128Sha256**: Use Aes256 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic128Sha256Rsa15**: Use Aes128 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />-   **Basic192**: Use Aes192 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic192Rsa15**: Use Aes192 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **Basic192Sha256**: Use Aes192 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic192Sha256Rsa15**: Use Aes192 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />-   **Basic256**: Use Aes256 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic256Rsa15**: Use Aes256 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **Basic256Sha256**: Use Aes256 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **Basic256Sha256Rsa15**: Use Aes256 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />-   **TripleDes**: Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.<br />-   **TripleDesRsa15**: Use TripleDes encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />-   **TripleDesSha256**: Use TripleDes for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />-   **TripleDesSha256Rsa15**: Use TripleDes for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br /><br /> The default value is **Basic256**.|  
|**Client certificate -  Thumbprint**|Specify the thumbprint of the X.509 certificate for authenticating this send port to services. You can select the thumbprint by navigating to the **My** store in the **Current User** location with the **Browse** button. **Note:**  You must install the client certificate into the **Current User** location of the user account for the send handler hosting this send port. <br /><br /> Minimum length: 0<br /><br /> Maximum length: 40<br /><br /> The default is an empty string.|  
|**Service certificate - Thumbprint**|Specify the thumbprint of the X.509 certificate for authenticating the service to which this send port sends messages. You can select the thumbprint navigating to the **Other People** store in the **Local Machine** location with the **Browse** button.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 40<br /><br /> The default is an empty string.|  
|**User name credentials**|Specify the credentials for sending messages. You can specify the property by clicking the **Edit** button. This option is valid only for the security configuration listed in the following section, "Enterprise Single Sign-On Supportability for the WCF-BasicHttp Send Adapter."<br /><br /> The default value is **Do not use Single Sign-On**.|  
  
## Enterprise Single Sign-On Supportability for the WCF-BasicHttp Send Adapter  
 The WCF-BasicHttp send adapter can redeem an SSO ticket from the SSO server to obtain the user credential only in the security configurations shown in the following table.  
  
|**Security mode**|**Transport client credential type**|**Message client credential type**|  
|-----------------------|------------------------------------------|----------------------------------------|  
|**Transport**|**Basic**|N/A|  
|**Transport**|**Digest**|N/A|  
|**TransportCredentialOnly**|**Basic**|N/A|  
|**TransportCredentialOnly**|**Digest**|N/A|  
|**Message**|N/A|**UserName**|  
|**TransportWithMessageCredential**|N/A|**UserName**|  
  
## See Also  
 [How to Configure a WCF-BasicHttp Send Port](../Topic/How%20to%20Configure%20a%20WCF-BasicHttp%20Send%20Port.md)   
 [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)   
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md)