---
title: "Prerequisites for the RosettaNet Loopback tutorial in BizTalk Server"
description: Prerequisites to step through the Loopback tutorial for the RosettaNet accelerator (BTARN) in BizTalk Server
ms.custom: 
ms.date: "08/09/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: tutorial
---

# Prepare for the tutorial

## Prerequisites
Before starting the Loopback tutorial:
  
-   [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md) the accelerator. You may have to add the btarnhttpreceive virtual directory to the Windows SharePoint managed path exclusion list in SharePoint Central Administration.  
  
-   Be sure the BizTalkServerIsolatedHost and BizTalkServerApplication hosts have the **Authentication trusted** option enabled. To verify, open the BizTalk Server Administration console, and expand **Hosts**. Right-click the host, select **Properties**, and check **Authentication Trusted** if it's not enabled.  

    If you have more than one host instance, then delete all but one host instance. For example, delete the BizTalk Server Isolated Host instance, and keep the BizTalkServerApplication host instance). This lets you select **Authentication Trusted** on the host associated with that instance, and then re-create the additional host instances.  
  
## Next step
 [Step 1: Create the Home Organization](step-1-create-the-home-organization.md)
