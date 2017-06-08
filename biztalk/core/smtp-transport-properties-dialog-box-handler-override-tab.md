---
title: "SMTP Transport Properties Dialog Box, Handler Override Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.smtp.transport.override"
helpviewer_keywords: 
  - "SMTP adapters, configuring"
  - "properties, SMTP adapters"
  - "configuring, SMTP adapters"
  - "SMTP adapters, properties"
ms.assetid: bfacf52d-37af-418c-8deb-e43ccb5de825
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SMTP Transport Properties Dialog Box, Handler Override Tab
In the **SMTP Transport Properties** dialog box, use the **Handler Override** tab to configure the send port for the Simple Mail Transfer Protocol (SMTP) adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**SMTP server name**|Specify the name of the SMTP server to use when sending messages.<br /><br /> Maximum length: 256|  
|**From (e-mail address)**|Specify the e-mail address to place on the SMTP From header.<br /><br /> Maximum length: 256|  
|**Authentication type**|Specify the type of authentication to use with the SMTP server.<br /><br /> Options:<br /><br /> -   (Default)<br />-   Do not authenticate<br />-   Basic authentication<br />-   Process account (NTLM)|  
|**User name**|Specify the user name to use for authentication with the SMTP server.<br /><br /> This property requires a value if Authentication type is Basic authentication.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Password**|Specify the password to use for authentication with the SMTP server.<br /><br /> This property requires a value if Authentication type is Basic authentication.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|