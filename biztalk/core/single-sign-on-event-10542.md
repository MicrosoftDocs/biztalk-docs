---
title: "Single Sign-On: Event 10542 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8e12444-b47c-4919-85b6-85c8e33b8342
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10542
## Details  

|                 |                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                          Enterprise Single Sign-On                                          |
| Product Version |                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                          |
|    Event ID     |                                                    10542                                                    |
|  Event Source   |                                                   ENTSSO                                                    |
|    Component    |                                                     CO                                                      |
|  Symbolic Name  |                                       SSO_WARN_APP_TICKETS_VALIDATED                                        |
|  Message Text   | Tickets cannot be redeemed for this application without being validated.%r<br /><br /> Application Name: %1 |

## Explanation  
 This Warning event indicates that application tickets cannot be redeemed without being validated. When application tickets are redeemed they can be validated or not validated. Validation improves security by comparing the name of the user who issued the ticket with the name of the user in the BizTalk message. If the names are not the same then validation fails. When a BizTalk message flows through an un-trusted host, the name of the user in the BizTalk message is changed to that of the un-trusted host. Validation ensures that the BizTalk message has only flowed through trusted hosts. This message means specifically that validation is required at the application system level (due to an SSO system option setting), but no validation information was provided by the caller.  

## User Action  
 To resolve this warning, do one or more of the following:  

- If you are using BizTalk Server, ensure that your message is flowing only through trusted hosts. This will reduce the risk of tampering with the data in the message.  

- If your scenario allows it, turn off validation for this application. Validation is an administration option which can be turned off for the system or just for this particular application.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [SSO Tickets](../core/sso-tickets.md)  

- [How to List the Properties of an Affiliate Application](../core/how-to-list-the-properties-of-an-affiliate-application.md)  

- [How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md)
