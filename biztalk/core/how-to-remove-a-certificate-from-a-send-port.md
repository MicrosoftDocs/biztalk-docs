---
title: "How to Remove a Certificate from a Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send ports, certificates"
  - "managing [send ports], certificates"
  - "certificates, deleting"
  - "deleting, certificates"
ms.assetid: fd93a83f-c2aa-4de2-9996-4ca4ec6d4a4c
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a Certificate from a Send Port
This topic describes how to use the BizTalk Server Administration console to remove a security certificate from a send port. When you do this, the send port will no longer encrypt messages; messages will be sent in clear text. Removing a certificate from a send port does not remove it from the certificate store.  
  
> [!NOTE]
>  The application developer can remove a security certificate from a send port during the development process by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To remove a certificate from a send port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to remove a certificate from a send port.  
  
3. Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Certificates**.  
  
4. Click **Remove certificate**, and then click **OK**.  
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)