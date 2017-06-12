---
title: "Configuring Alert Queue Options and Notifications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f78afbf9-6e27-4887-8424-f265fbd8448a
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Alert Queue Options and Notifications
The ESB Management Portal uses the ESB Alert Service to generate alerts as fault messages arrive at the portal, and it uses the ESB Notification Service to queue and send alert notifications to users that subscribe to alerts. You can edit the settings used by these services in the ESB Management Portal.  
  
### To configure the settings for the ESB Alert Service  
  
1.  Ensure that you log on to the portal using an account that is a member of the Microsoft BizTalk Server Administrators account group (of which portal administrators are automatically a member).  
  
2.  Point to the **Admin** tab on the portal main menu, and then click **Fault Settings** to open the portal [Fault Settings Page](../esb-toolkit/fault-settings-page.md).  
  
3.  In the **Alert Queue Options** section, select or clear the **Enable Alert Queue Service** check box to enable or disable the service.  
  
4.  If you enable the service, edit the values in the remaining controls to suit our requirements. The service interacts with Microsoft Active Directory, so you must specify the appropriate LDAP (Lightweight Directory Access Protocol) connection string. You can also specify the queue batch size and polling interval.  
  
5.  Click **Save** to save the new settings.  
  
### To configure the settings for the ESB Alert Email Notification service  
  
1.  Ensure that you log on to the portal using an account that is a member of the BizTalk Server Administrators account group (of which portal administrators are automatically a member).  
  
2.  Point to the **Admin** tab on the portal main menu, and then click **Fault Settings** to open the portal [Fault Settings Page](../esb-toolkit/fault-settings-page.md).  
  
3.  In the **Alert Email Options** section, select or clear the **Enable Alert Email Service** check box to enable or disable the service.  
  
4.  If you enable the service, edit the values in the remaining controls to suit our requirements. Specify the e-mail server name and the "from" address, change the polling interval and batch size as required, and specify the path to Extensible Stylesheet Language Transformations (XSLT) files that the service uses.  
  
5.  Click **Save** to save the new settings.