---
title: "SSO Tickets | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tickets [SSO]"
ms.assetid: acf01422-4696-4301-b85f-7026e792bb5c
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO Tickets
In an enterprise environment, where a user interacts with various systems and applications, it is very likely that the environment does not maintain the user context through multiple processes, products, and computers. This user context is crucial to provide single sign-on capabilities, as it is necessary to verify who initiated the original request. To overcome this problem Enterprise Single Sign-On (SSO) provides an SSO ticket (not a Kerberos ticket) that applications can use to get the credentials that correspond to the user who made the original request. SSO tickets are not enabled by default. For more information about enabling tickets, see [How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md).  
  
 The SSO system issues a ticket when requested by an authenticated Windows user. The SSO system can issue a ticket for the user making the request or for a remote user. A ticket contains the encrypted domain and username of the current user, and the ticket expiration time. After the SSO system issues a ticket, it expires in two minutes by default. SSO administrators can modify the expiration time for tickets. The SSO Administrator can also set the ticket timeout at the Affiliate Application level. For more information, see [How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md).  
  
 After an application verifies the identity of the original requester, the application redeems the ticket to obtain the credentials of the user who initiated the request affiliate application. An application can redeem tickets from the SSO system in one of two ways:  
  
- **Redeem only.** When an application initiates a request to redeem a ticket, the request must contain the name of the affiliate application to connect to, and the ticket itself. Only application administrators for the specific affiliate application, SSO affiliate administrators, or SSO administrators can redeem a ticket. You should use **Redeem only** when there is a trusted sub-system between the application that issued the ticket and the application redeeming the ticket. Only an application administrator for the specified affiliate application can redeem the ticket for a user.  
  
- **Validate and redeem.** Tickets contain information about the user for whom the SSO system is performing the credential look-up. In this case, the SSO service verifies that the sender of the original message and the user of the ticket are the same before the system redeems the ticket. Microsoft BizTalk Server adapter scenarios leverage this mechanism.  
  
  An SSO administrator can disable ticket timeouts on a per affiliate application basis. While this was not recommended in previous releases, this release supports the use of per affiliate application ticket timeout. This option allows you to set the ticket timeouts at the Affiliate Application level. If this is not specified, the ticket timeout specified at the global level is used.  
  
  An SSO affiliate administrator can specify that tickets are allowed and that validation of the ticket is required on a per affiliate application basis. However, if the SSO administrator specifies at the SSO system level that the validation of tickets is required, the SSO affiliate administrator cannot turn off this option at the affiliate application level.  
  
> [!IMPORTANT]
>  When using SSO ticketing, you must ensure that the ticket timeout value is long enough to last between the time when the ticket is issued to the time that it is redeemed.  
  
## See Also  
 [Managing User Mappings](../core/managing-user-mappings.md)