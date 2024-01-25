---
title: "Configure the SSO Tickets"
description: Use SSO Administrations or a command line to to allow and validate Enterprise Single sign-on tickets at the system level, and for affiliate applications in BizTalk Server.
ms.custom: ""
ms.date: "01/08/2019"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Configure the SSO Tickets in BizTalk Server
You can use Enterprise Single Sign-On (SSO) Administration MMC or the command line to control ticket behavior for the entire single sign-on system. Using this tools, you can allow tickets and validate SSO tickets.  
  
## Before you begin

- If SSO Administration is installed on a remote computer, you can run a remote [IssueTicket](/biztalk/core/technical-reference/issoticket-issueticket-method) operation. All traffic between the SSO Administration module and the Runtime module (ENTSSO service) is encrypted.  
  
- Using the ssomanage.exe command line utility, you can enter the ticket timeout at the Affiliate Application level. You can do this only when an update of the application is made, not when the application is created.
  
- Only users in the SSO Administrator group can configure tickets at the SSO system-level and at the Affiliate Application level.  
  
- If ticketing is disabled at the system-level, it can't be used at the Affiliate Application level. It's possible to enable tickets at the system level, and disable them at the Affiliate Application level.  
  
- If validation is enabled at the system-level, tickets must be validated at the Affiliate Application level. It's possible to disable validation at the system-level, and enable it at the Affiliate Application level.  
  
- If ticket timeout is entered at the system-level and the Affiliate Application level, the one entered at the Affiliate Application level determines the ticket expiration time.  
  
For more information about tickets and tickets validation, see [SSO Tickets](../core/sso-tickets.md).  
  
## Allow Affiliate Application tickets using SSO Administration  
  
1.  From the **Start** menu, select **All Programs** > **Microsoft Enterprise Single Sign-On** > **SSO Administration**.
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Affiliate Applications** node.  
  
3.  Right-click **Affiliate Application** > **Properties**.  
  
4.  Choose the **Options** tab.  
  
5.  Select **Allow Tickets** and enter the ticket timeout you want.  
  
## Allow and validate SSO system-level tickets using the command line  
  
1. Open a command prompt (Start menu > type **command prompt** > select **Command Prompt**).

    > [!TIP]
    >  On a system that supports User Account Control (UAC), you may need to open the command prompt with Administrative privileges (right-click **Command Prompt** > **Run as administrator**).
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is `\Program Files\Common Files\Enterprise Single Sign-On`. For example, enter: 

    `cd C:\Program Files\Common Files\Enterprise Single Sign-On`
  
3. Type `ssomanage -tickets <allowed yes/no> <validate yes/no>`, where *\<allowed yes/no\>* indicates whether tickets are allowed or not, and *\<validate yes/no\>* indicates whether tickets need to be validated after they're redeemed.  
  
    You can use `yes`, `no`, `on`, or `off` to allow and/or validate tickets. These words are case independent, and must be used regardless of your language settings.
  
## See Also

[Understanding SSO](../core/understanding-sso.md)   
[Using SSO](../core/using-sso.md)