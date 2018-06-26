---
title: "How to Configure the SSO Tickets | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [SSO], configuring tickets"
  - "SSO, tickets"
  - "tickets [SSO], configuring"
ms.assetid: 32f0384b-ac79-4cce-b3f5-f4f8a73a673a
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the SSO Tickets
You can use the MMC Snap-In or the command line to control ticket behavior for the entire Single Sign-On system, including whether to allow tickets, and whether the system must validate the tickets.  
  
 You can use Yes, No, On, or Off to indicate whether to allow and/or validate tickets. These words are case independent, and must be used regardless of your language settings.  
  
 If you have the SSO Administration feature installed on a remote computer, remote IssueTicket operation can be performed. Note that all traffic between the SSO Administration module and the Runtime module (ENTSSO service) is encrypted.  
  
 Using the command line utility, ssomanage.exe, you can specify the ticket timeout at the Affiliate Application level only when an update of the Application is performed,  not at creation time.  
  
 Only an SSO Administrator can configure tickets at the SSO System level and at the Affiliate Application level.  
  
 If ticketing is disabled at the system level, it cannot be used at the Affiliate Application level either. It is possible to enable tickets at the system level and disable it at the Affiliate Application level.  
  
 If validation is enabled at the system level, validation of tickets are required at the Affiliate Application level as well. It is possible to disable validation at the system level and enable it at the Affiliate Application level.  
  
 If Ticket timeout is specified both at the System level and the Affiliate Application level, the one specified at the Affiliate Application level is used to determine the ticket expiry time.  
  
 For more information about tickets and tickets validation, see [SSO Tickets](../core/sso-tickets.md).  
  
### To configure the Enterprise Single Sign-On tickets using the MMC Snap-In for the Affiliate Application  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Affiliate Applications** node.  
  
3.  Right-click **Affiliate Application**, and then click **Properties**.  
  
4.  Click the **Options** tab.  
  
5.  Select **Allow Tickets** and configure the ticket timeout as appropriate.  
  
### To configure the Enterprise Single Sign-On system-level tickets using the command line  
  
1. On the **Start** menu, click **run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssomanage –tickets \<allowed yes/no\> *\<validate yes/no\>**<em>, where *\<allowed yes/no\></em> indicates whether tickets will be allowed or not, and *\<validate yes/no\>* indicates whether tickets will need to be validated after they are redeemed.  
  
   > [!NOTE]
   >  You can use yes, no, on, or off to indicate whether to allow and/or validate tickets. These words are case independent, and must be used regardless of your language settings.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [Understanding SSO](../core/understanding-sso.md)   
 [Using SSO](../core/using-sso.md)