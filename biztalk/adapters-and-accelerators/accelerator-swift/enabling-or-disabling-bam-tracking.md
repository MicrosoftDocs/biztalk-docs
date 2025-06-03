---
description: "Learn more about: Enabling or Disabling BAM Tracking"
title: "Enabling or Disabling BAM Tracking"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Enabling or Disabling BAM Tracking
You can enable or disable BAM tracking at any point, even while the Message Repair and New Transmission process has transactions in process. However, if you disable BAM tracking while transactions are in process, the BAM data may be incomplete for those transactions. If this occurs, the history table will still contain accurate data for all instances.  
  
 For information about enabling or disabling BAM tracking as part of the A4SWIFT component configuration process, see [Setting A4SWIFT Properties](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md).  
  
### To enable or disable BAM Tracking  
  
1.  In the Profile Web Client, right-click **BizTalk Accelerator for SWIFT** in the console tree, and then click **Properties**.  
  
2.  In the Global Properties dialog box, disable BAM tracking by deselecting **Enable BAM Tracking**, or enable BAM tracking by selecting it.  
  
3.  Click **OK**.  
  
4.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, and then **Platform Settings**. Click **Host Instances**.  
  
5.  In the details pane, right-click the host instance , and then click **Restart**.  
  
## See Also  
 [Setting A4SWIFT Properties](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)
