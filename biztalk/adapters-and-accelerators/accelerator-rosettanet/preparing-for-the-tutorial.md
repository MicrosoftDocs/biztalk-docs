---
title: "Preparing for the Tutorial | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "loopback tutorial, pre-requisites"
ms.assetid: 3e26696c-86c5-448b-9cd6-bfd4a279151a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Preparing for the Tutorial
Before you start the Loopback tutorial, you must do the following:  
  
-   Make sure that you have performed the configuration steps described in "Additional Configuration of Microsoft BizTalk Accelerator for RosettaNet" section of the [Installation Guide](http://go.microsoft.com/fwlink/?LinkId=188560). This includes adding the btarnhttpreceive virtual directory to the Windows SharePoint Services managed path exclusion list in SharePoint Central Administration.  
  
-   Make sure that BizTalkServerIsolatedHost and BizTalkServerApplication hosts have the **Authentication trusted** option enabled. For information about configuring [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] hosts, see [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Help. To verify the setting of the **Authentication trusted** option, in the **Hosts** folder of [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Administration Console, right-click the host, and then click **Properties**. In the Host Properties dialog box, verify that **Authentication Trusted** is selected. If not, select **Authentication Trusted**. If you have more than one host instance, you will have to delete all but one host instance (for example, delete the BizTalk Server Isolated Host instance, keeping the BizTalkServerApplication host instance) in order to select **Authentication Trusted** on the host associated with that instance, and then re-create the additional host instances.  
  
## See Also  
 [Step 1: Create the Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-the-home-organization.md)