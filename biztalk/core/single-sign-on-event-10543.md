---
description: "Learn more about: Single Sign-On: Event 10543"
title: "Single Sign-On: Event 10543"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10543
## Details  

| Field | Error Details |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                               Enterprise Single Sign-On                                                                |
| Product Version |                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                               |
|    Event ID     |                                                                         10543                                                                          |
|  Event Source   |                                                                         ENTSSO                                                                         |
|    Component    |                                                                           CO                                                                           |
|  Symbolic Name  |                                                           SSO_WARN_ORIGINAL_TICKET_VALIDATED                                                           |
|  Message Text   | The ticket was issued with validation required. It cannot be redeemed for this application without being validated.%r<br /><br /> Application Name: %1 |

## Explanation  
 This Warning event indicates that an application ticket was issued with validation required. Tickets cannot be redeemed without being validated. Validation of the ticket is on a per affiliate application basis.  

## User Action  
 To resolve this warning, do the following:  

- If you are using Enterprise Single Sign-On, ensure that your message is flowing only through trusted hosts. This will reduce the risk of tampering with the data in the message.  

- If your scenario allows it, turn off validation for this application. Validation is an administration option which can be turned off for the system or just for this particular application.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [SSO Tickets](../core/sso-tickets.md)  

- [How to List the Properties of an Affiliate Application](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md)
