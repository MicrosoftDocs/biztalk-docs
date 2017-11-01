---
title: "How to Configure the Enterprise Single Sign-On Tickets | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4650ce49-1d02-4ce5-841c-ad4262d60e9b
caps.latest.revision: 3
---
# How to Configure the Enterprise Single Sign-On Tickets
You can use the Microsoft Management Console (MMC) Snap-In or the command line to control ticket behavior for the entire Single Sign-On (SSO) system, including whether to allow tickets, and whether the system must validate the tickets. You can use **Yes**, **No**, **On**, or **Off** to indicate whether to allow or validate tickets. These words are case independent, and they must be used regardless of your language settings.  
  
 If you have the SSO Administration feature installed on a remote computer, you can perform remote IssueTicket operation. Note that all traffic between the SSO Administration module and the Runtime module (ENTSSO service) is encrypted.  
  
 By using the command-line utility, ssomanage.exe, you can specify the ticket time-out at the affiliate application level only when an update of the application is performed, not at creation time. Only an SSO Administrator can configure tickets at the SSO system level and at the affiliate application level. If ticketing is disabled at the system level, it cannot be used at the affiliate application level either. You can enable tickets at the system level and disable them at the affiliate application level. If validation is enabled at the system level, validation of tickets is required at the affiliate application level also. You can disable validation at the system level and enable it at the affiliate application level.  
  
 If ticket time-out is specified both at the system level and the affiliate application level, the one specified at the affiliate application level is used to determine the ticket expiry time.  
  
 For more information about tickets and ticket validation, see [SSO Tickets](../esso/sso-tickets.md).  
  
### To configure the SSO tickets using the MMC Snap-In for the Affiliate Application  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Affiliate Applications** node.  
  
3.  Right-click **Affiliate Application**, and then click **Properties**.  
  
4.  Click the **Options** tab.  
  
5.  Select **Allow Tickets** and configure the ticket time-out as appropriate.  
  
### To configure the SSO system-level tickets using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –tickets <allowed yes/no>``<validate yes/no>`, where *\<allowed yes/no>* indicates whether tickets will be allowed or not, and *\<validate yes/no>* indicates whether tickets must be validated after they are redeemed.  
  
    > [!NOTE]
    >  You can use **yes**, **no**, **on**, or **off** to indicate whether to allow or validate tickets. These words are case independent, and they must be used regardless of your language settings.  
  
## See Also  
 [Enterprise Single Sign-On Basics](../esso/enterprise-single-sign-on-basics.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)