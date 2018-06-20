---
title: "How to Configure Backup Transport Options for a Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring, send ports"
  - "managing [send ports], configuring"
  - "configuring, backing up [send ports]"
  - "managing [send ports], backup options"
  - "send ports, configuring"
  - "send ports, backup options"
ms.assetid: f05f57a6-e62b-4640-a6e2-cb73e9de2a14
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Backup Transport Options for a Send Port
This topic describes how to use the BizTalk Server Administration console to configure backup transport options for a send port. The backup transport that you specify takes effect in the event the primary transport fails to function. Configuring the primary transport is described in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).  
  
> [!NOTE]
>  For dynamic ports, there are not properties available to configure because transport options are automatically determined at run time.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To specify transport options for a send port  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure backup transport options for a send port.  
  
3. Expand **Send Ports**, right-click the send port to configure, click **Properties**, and then click **Backup Transport**.  
  
4. Configure backup transport properties as described in the following table, and then click **OK**.  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Type**|From the drop-down list, select the appropriate backup transport type, or transport protocol. If the port is a solicit-response port, only transport types that support solicit-response are available in the list.|  
   |**Configure**|After you select the backup transport type, click **Configure**, and then configure transport properties. For more information about configuring the properties, click **Help**.|  
   |**Send handler**|From the drop-down list, select the host instance on which the send adapter is running.|  
   |**Retry count**|Specify the number of times for the send port to resend a message on message failure. The default is 3; the allowed range is from 0 to 1,000.|  
   |**Retry interval**|Specify the interval in minutes between message resend attempts. The default is 5; the allowed range is from 0 to 525,600.|  
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)