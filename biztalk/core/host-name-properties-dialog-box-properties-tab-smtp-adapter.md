---
title: "&lt;Host Name&gt; Properties Dialog Box, Properties Tab (SMTP Adapter) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.smtp.props1"
helpviewer_keywords: 
  - "properties, SMTP adapters"
  - "SMTP adapters, properties"
ms.assetid: a4e09d76-8304-4eb1-b23e-0dd2fe7b9388
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# &lt;Host Name&gt; Properties Dialog Box, Properties Tab (SMTP Adapter)
Use the **Properties** tab to configure the send handler for the Simple Mail Transfer Protocol (SMTP) adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**SMTP server name**|Specify the name of the SMTP server to use when sending messages.<br /><br /> This property requires a value.<br /><br /> Maximum length: 256|  
|**From (e-mail address)**|Required. Specify the e-mail address to place on the SMTP From header.<br /><br /> Maximum length: 256|  
|**Authentication type**|Specify the type of authentication to use with the SMTP server.<br /><br /> Options:<br /><br /> -   Do not authenticate<br />-   Basic authentication<br />-   Process account (NTLM)<br /><br /> Default value: Process account (NTLM)|  
|**User name**|Specify the user name to use for authentication with the SMTP server.<br /><br /> This property requires a value if Authentication type is Basic authentication.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Password**|Specify the password to use for authentication with the SMTP server.<br /><br /> This property requires a value if Authentication type is Basic authentication.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
  
## See Also  
 [How to Configure an SMTP Send Handler](../core/how-to-configure-an-smtp-send-handler.md)