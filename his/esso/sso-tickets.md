---
title: "SSO Tickets | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50c09c4d-7a21-481f-90fd-5ad5495ae1b5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SSO Tickets
In an enterprise environment, where a user interacts with various systems and applications, it is very likely that the environment does not maintain the user context through multiple processes, products, and computers. This user context is crucial to providing single sign-on capabilities because it is necessary to verify who initiated the original request. To overcome this problem, Enterprise Single Sign-On (SSO) provides an SSO ticket (not a Kerberos ticket) that applications can use to obtain the credentials that correspond to the user who made the original request. By default, SSO tickets are not enabled. For more information about enabling tickets, see [How to Configure the Enterprise Single Sign-On Tickets](../esso/how-to-configure-the-enterprise-single-sign-on-tickets.md).  
  
 The SSO system issues a ticket when requested by an authenticated Windows user. The SSO system can only issue a ticket for the user making the request (you cannot request a ticket for other users). A ticket contains the encrypted domain and user name of the current user, and the ticket expiration time. After the SSO system issues a ticket, the ticket expires in two minutes by default. SSO administrators can modify the expiration time for tickets. For more information, [How to Configure the Enterprise Single Sign-On Tickets](../esso/how-to-configure-the-enterprise-single-sign-on-tickets.md).  
  
 After an application verifies the identity of the original requester, the application redeems the ticket to obtain the credentials of the user who initiated the request to the affiliate application. An application can redeem tickets from the SSO system in one of three ways:  
  
- **Redeem only.** When an application initiates a request to redeem a ticket, the request must contain the name of the affiliate application to connect to, and the ticket itself. Only application administrators for the specific affiliate application, SSO affiliate administrators, or SSO administrators can redeem a ticket. You should use **Redeem only** when there is a trusted sub-system between the application that issued the ticket and the application that is redeeming the ticket. Only an application administrator for the specified affiliate application can redeem the ticket for a user.  
  
- **Validate and redeem.** Tickets contain information about the user for whom the SSO system is performing the credential look-up. In this case, the SSO service verifies that the sender of the original message and the user of the ticket are the same before the system redeems the ticket.  
  
  An SSO administrator can disable ticket time-outs on a per-affiliate application basis. However, this is not recommended, as the ticket would never expire for this application. In scenarios that require that you disable ticket time-outs, ensure that there is a secure end-to-end trusted sub-system maintained between the front-end where the SSO system issues the ticket to the adapter where the SSO ticket redeems the ticket.  
  
  An SSO affiliate administrator can specify that tickets are allowed and that validation of the ticket is required on a per affiliate application basis. However, if the SSO administrator specifies at the SSO system level that the validation of tickets is required, the SSO affiliate administrator cannot turn off this option at the affiliate application level.  
  
> [!IMPORTANT]
>  When using SSO ticketing, you must ensure that the ticket time-out value is long enough to last between the time when the ticket is issued to the time that it is redeemed.  
  
## See Also  
 [Managing User Mappings](../esso/managing-user-mappings.md)   
 [Enterprise Single Sign-On Basics](../esso/enterprise-single-sign-on-basics.md)   
 [How to Configure the Enterprise Single Sign-On Tickets](../esso/how-to-configure-the-enterprise-single-sign-on-tickets.md)