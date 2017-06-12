---
title: "WCF Adapters Transport Properties Dialog Box, General Tab, Identity Editor | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-adapters.transport.general.identity"
helpviewer_keywords: 
  - "Identity Editory [WCF adapters]"
  - "properties, WCF adapters"
  - "WCF adapters, properties"
  - "WCF adapters, Identity Editor"
ms.assetid: 47a04277-71a9-4bc3-b2bb-67aa61007656
caps.latest.revision: 44
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapters Transport Properties Dialog Box, General Tab, Identity Editor
Use the **Identity Editor** dialog box to configure the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the **Endpoint Identity** property differ according to the security configuration on the **Security** tab. For more information about how to setup the **Identity** property for WCF services, see "Specifying the Identity of a Service for Authentication" listed in the See Also section of this topic.  
  
|Use this|To do this|  
|--------------|----------------|  
|**1. DNS**|Specify a DNS identity of the service to which this send port sends messages.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
|**2. Service principal name**|Specify a server principal name (SPN) identity, which is the principal name to uniquely identify an instance of the service to which this send port sends messages.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
|**3. User principal name**|Specify a user principal name (UPN) identity, which is the logon name type of a user on a network. The user principal name consists of the user object name used in Active Directory, followed by the at symbol (@) and then, typically, the Domain Name System parent domain. For example, JeffSmith in the Fabrikam.com domain tree might have the user principal name jeffsmith@fabrikam.com.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
|**4. RSA**|Specify the RSA public key value of an X.509 certificate used to authenticate the service to which this send port sends messages. An RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or your own RSA key value. This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
|**5. Certificate (Base-64)**|Specify a Base64 encoding of an X.509 certificate used to validate the service that this send port consumes.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
|**Find type**|Specify the type of X.509 search to be executed. The type contained in the **Find value** property must satisfy the requirements of the specified **Find type** value. Valid values include the following:<br /><br /> -   **FindByThumbPrint**<br />-   **FindBySubjectName**<br />-   **FindBySubjectDistinguishedName**<br />-   **FindByIssuerName**<br />-   **FindByIssuerDistinguishedName**<br />-   **FindBySerialNumber**<br />-   **FindByTimeValid**<br />-   **FindByTimeNotYetValid**<br />-   **FindByTimeExpired**<br />-   **FindByTemplateName**<br />-   **FindByApplicationPolicy**<br />-   **FindByCertificatePolicy**<br />-   **FindByExtension**<br />-   **FindByKeyUsage**<br />-   **FindBySubjectKeyIdentifier**<br /><br /> The default value is **FindBySubjectDistinguishedName**.|  
|**Find value**|Specify the value to search for in the X.509 certificate store. The type contained in this property must satisfy the requirements of the specified **Find type** value.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
|**Is chain included?**|A Boolean value that specifies if the validation is done using a certificate chain.<br /><br /> The default is **False**.|  
|**Store location**|Specify the location of the certificate store that this send port can use to validate the service. Valid values include the following:<br /><br /> -   **LocalMachine**: The certificate store assigned to the local machine.<br />-   **CurrentUser**: The certificate store assigned to the current user. **Note:**      To use the **CurrentUser** location, you must install the certificate into the **Current User** location of the user account configured for the send handler hosting this send port.<br /><br /> The default value is **LocalMachine**.|  
|**Store name**|Specify the name of the X.509 certificate store to open.<br /><br /> Valid values include the following:<br /><br /> -   **AddressBook**: Certificate store for other users.<br />-   **AuthRoot**: Certificate store for third-party certification authorities (CAs).<br />-   **CertificateAuthority**: Certificate store for intermediate CAs.<br />-   **Disallowed**: Certificate store for revoked certificates.<br />-   **My**: Certificate store for personal certificates.<br />-   **Root**: Certificate store for trusted root CAs.<br />-   **TrustedPeople**: Certificate store for directly trusted people and resources.<br />-   **TrustedPublisher**: Certificate store for directly trusted publishers.<br /><br /> The default value is **My**.|  
  
## How to Remove an Identity Setting  
 To remove an identity setting for a send port, delete all the values of the **1. DNS**, **2. Service principal name**, **3. User principal name**, **4. RSA**, **5. Certificate (Base-64)**, and **Find value** properties.  
  
## See Also  
 [The \<identity> element](http://go.microsoft.com/fwlink/?LinkId=75747)   
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md)   
 [Specifying the Identity of a Service for Authentication](http://go.microsoft.com/fwlink/?LinkId=88889)