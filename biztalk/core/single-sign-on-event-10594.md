---
description: "Learn more about: Single Sign-On: Event 10594"
title: "Single Sign-On: Event 10594"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10594
## Details  
  
| Field | Error Details|
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
