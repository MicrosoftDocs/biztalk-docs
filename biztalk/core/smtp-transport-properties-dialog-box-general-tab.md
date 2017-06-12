---
title: "SMTP Transport Properties Dialog Box, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.smtp.transport.general"
helpviewer_keywords: 
  - "SMTP adapters, configuring"
  - "properties, SMTP adapters"
  - "configuring, SMTP adapters"
  - "SMTP adapters, properties"
ms.assetid: 3c38713b-853b-4f35-bce1-795b73e07d43
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SMTP Transport Properties Dialog Box, General Tab
In the **SMTP Transport Properties** dialog box, use the **General** tab to configure the send port for the Simple Mail Transfer Protocol (SMTP) adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**To**|Required. Specify the e-mail address for where to send messages.<br /><br /> You can specify more than one address.<br /><br /> Maximum length: 256|  
|**CC**|Specify the e-mail address to send the carbon copy of the message(s).<br /><br /> You can specify more than one address.<br /><br /> Maximum length: 1,024|  
|**Subject**|Specify the subject header for the message(s).<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Notification**|Specify the type of notification receipt. You can select one or both types of receipts. Notification receipt types are:<br /><br /> -   Read Receipt. Confirmation e-mail is sent when the message is read.<br />-   Delivery Receipt. Confirmation e-mail is sent when the message is delivered.|  
  
## See Also  
 [Restrictions on the SMTP To Property](../core/restrictions-on-the-smtp-to-property.md)