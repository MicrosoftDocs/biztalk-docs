---
title: "HTTP Transport Properties Dialog Box, Authentication Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.http.transport.authentication"
helpviewer_keywords: 
  - "HTTP adapters, configuring"
  - "authenticating, HTTP adapters"
  - "configuring, HTTP adapters"
  - "HTTP adapters, authenticating"
ms.assetid: d9d510e4-c34f-4ef3-817e-62e9ed199e24
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Transport Properties Dialog Box, Authentication Tab
In the **HTTP Transport Properties** dialog box, use the **Authentication** tab to configure the send port for the HTTP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Authentication Type**|Specify the type of authentication to use with the destination server.<br /><br /> Options:<br /><br /> -   Anonymous<br />-   Basic<br />-   Digest<br />-   Kerberos<br /><br /> Default Value: Anonymous|  
|**Credentials**|Specify the type of credentials to use.<br /><br /> Only available if the Authentication Type is Basic or Digest.<br /><br /> Options:<br /><br /> -   **Do Not Use Single Sign-On**<br />     **User name**<br />     The user name to use for authentication with the destination server. If the Authentication Type property is Anonymous or Kerberos, this option is disabled. This property requires a value if Basic or Digest is selected, and Enterprise Single Sign-On is not used.<br />     Minimum length: 0<br />     Maximum length: 256<br />     **Password**<br />     The password to use for authentication with the destination server. If the Authentication Type property is Anonymous or Kerberos, this option is disabled. This property requires a value if Basic or Digest is selected, and Single Sign-On is not used.<br />     Minimum length: 0<br />     Maximum length: 256<br />-   **Use Single Sign-On**<br />     Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br />     **Affiliate Application**<br />     Specifies the affiliate application to use for Single Sign-On.<br />     Choose the applications that you want to include in Single Sign-On.<br />     Minimum length: 0<br />     Maximum length: 256|  
|**SSL client certificate thumbprint**|Specify the thumbprint of the client certificate to use for establishing a Secure Sockets Layer (SSL) connection.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 59|  
  
## See Also  
 [Configuring an HTTP Send Port](../core/configuring-an-http-send-port.md)