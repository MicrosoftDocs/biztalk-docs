---
description: "Learn more about: Enabling BAM Tracking"
title: "Enabling BAM Tracking"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Enabling BAM Tracking
[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] supports enhanced tracking using BizTalk Activity Monitoring (BAM). You enable tracking as part of the global properties of the BTARN configuration. After you enable tracking, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracks all messages for all agreements. By default, tracking is enabled.  
  
 For more information about tracking, see [Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md).  
  
### To enable or disable BAM tracking  
  
1. Click **Start**, point to **Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2. Right-click the [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] node in the scope pane, and then click **Properties**.  
  
3. In the **Global Properties** dialog box, select **Enable BAM Tracking** to enable tracking, or clear this option to disable it.  
  
> [!IMPORTANT]
>  Whenever you change the enable flag to enable or disable tracking, you have to restart all services on which the public processes and the HTTP adapter are running. This includes the host service and the isolated host service.  
  
## See Also  
 [Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md)   
 [Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)   
 [Administering the BTARN Configuration](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)
