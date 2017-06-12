---
title: "SOAP Transport Properties Dialog Box, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.soap.transport.general"
helpviewer_keywords: 
  - "SOAP adapters, properties"
  - "properties, SOAP adapters"
ms.assetid: 28abbac8-d51d-4094-a5fb-b62df2d350b8
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Transport Properties Dialog Box, General Tab
In the **SOAP Transport Properties** dialog box, use the **General** tab to configure the send port for the SOAP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Web Service URL**|Specify the address of the Web service you want to call.|  
|**Authentication**|Indicate the authentication method used by the Web service you are calling.<br /><br /> Options:<br /><br /> -   Anonymous<br />-   Basic<br />-   Digest<br />-   NTLM|  
|**Credentials**|Specify the type of credentials to use.<br /><br /> Only available if the Authentication type is Basic or Digest.<br /><br /> Options:<br /><br /> -   Do Not Use Single Sign-On<br />     **User name**<br />     The user name to use for authentication with the destination server. If the Authentication type property is Anonymous or Kerberos, this option is disabled. This property requires a value if Basic or Digest is selected, and Enterprise Single Sign-On is not used.<br />     Minimum length: 0<br />     Maximum length: 256<br />     **Password**<br />     The password to use for authentication with the destination server. If the Authentication type property is Anonymous or Kerberos, this option is disabled. This property requires a value if Basic or Digest is selected, and Single Sign-On is not used.<br />     Minimum length: 0<br />     Maximum length: 256<br />-   Use Single Sign-On<br />     Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br />     **Affiliate Application**<br />     Specifies the affiliate application to use for Single Sign-On. For information about populating this list, see the appropriate topics in See Also.<br />     Minimum length: 0<br />     Maximum length: 256|  
|**Client Certificate Thumbprint**|Specify the thumbprint of the client certificate to use for establishing a connection.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 59|  
  
## See Also  
 [How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md)   
 [Using SSO](../core/using-sso.md)