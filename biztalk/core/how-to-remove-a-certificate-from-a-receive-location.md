---
title: "How to Remove a Certificate from a Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "certificates, receive locations"
  - "receive locations, certificates"
  - "managing [receive locations], certificates"
ms.assetid: 717d41bf-4260-4df4-9d0a-07243bb9b12c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a Certificate from a Receive Location
This topic describes how to use the BizTalk Server Administration console to remove a security certificate from a receive location. When you do this, the receive location will no longer encrypt messages; messages will be sent in clear text. Removing a certificate from a receive location does not remove it from the certificate store.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To remove a certificate from a receive location  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to remove a certificate from a receive location.  
  
3. Expand **Receive Locations**, right-click the receive location, click **Properties**, and then click **Certificates**.  
  
4. Click **Remove certificate**, and then click **OK**.  
  
## See Also  
 [Managing Receive Locations](../core/managing-receive-locations.md)