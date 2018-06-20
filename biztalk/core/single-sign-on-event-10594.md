---
title: "Single Sign-On: Event 10594 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f4c6041-39a8-49bc-b39e-66cb6eb2efae
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10594
## Details  
  
|                 |                                                                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                 Enterprise Single Sign-On                                                                                  |
| Product Version |                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                 |
|    Event ID     |                                                                                           10594                                                                                            |
|  Event Source   |                                                                                           ENTSSO                                                                                           |
|    Component    |                                                                                            N/A                                                                                             |
|  Symbolic Name  |                                                                              SSO_WARN_TICKET_VALIDATE_FAILED                                                                               |
|  Message Text   | Validation of the ticket failed. The sender name must match that of the ticket issuer.%r<br /><br /> Application Name: %1%r<br /><br /> Ticket Issued By: %2%r<br /><br /> Sender Name: %3 |
  
## Explanation  
 In order for a ticket to be validated, the Ticket Issued By and Sender Name fields (in the warning message) must match. If, however, the message is sent through a BizTalk untrusted host, the Sender Name gets changed to the name of the BizTalk untrusted host, and the ticket will not validate.  
  
## User Action  
 If you are using Enterprise Single Sign-On, ensure that your message is flowing only through BizTalk trusted hosts. This will reduce the risk of tampering with the data in the message.  
  
 If you fully understand the security implications for your scenario, you can turn off validation for this application. Note that validation is an administration option which can be turned off for the system or just for this particular application.